##### **Install Elasticsearch**
- Link web site: [elastic.io](https://www.elastic.co/docs/deploy-manage/deploy/self-managed/install-elasticsearch-with-rpm) 
- Link login Kibana : http://172.16.3.3:5601/
- Link login Elasticsearch: https://172.16.3.3:9200/
- Note: all file download & install via directory U01 on vm Monitor_Server (virtual machine running oracle linux 8 in [Clear Sky Cloud](https://console3.clearsky.vn/#provision-tab))

##### **Introduction**

Elasticsearch, Logstash, and Kibana, which 3 open-source applications developed, managed, and supported by Elastic, formed the foundation of the ELK Stack.

**Elasticsearch** is a the whole text search and evaluation engine which employs the Apache Lucene free search engine. It includes a distributed, multitenant full-text search engine, an HTTP web interface, and schema-free documents in JSON.  
**Logstash** is a logging aggregator that accepts data from a variety of input sources, applies various transformations and enhancements, and then sends the data to a variety of supported output destinations.  
**Kibana** is a visualization layer that sits on above Elasticsearch, which allowing users to examine and visualize data. Last but not least, Beats are simple agents which are put on edge hosts to collect various types of data before forwarding it into the stack.

**How to Set Up RHEL to Install ELK S**tack****  

Let’s install the ELK stack on the Oracle Linux server. Rocky and RHEL, as well as other RHEL-based distributions, can be installed using the same steps. Let’s get a brief overview of what each component:

- Elasticsearch saves the logs sent by clients.

- These logs are processed by Logstash.

- Kibana provides a web interface for inspecting and analyzing logs.

We will need to install Java JDK version 21, the most recent version stable release, which is required by the ELK components.

You may want to first check the [Java downloads page](https://www.oracle.com/java/technologies/downloads/) to see if a newer version is available.

**Step 1:** You need to first make sure the your server is up to date suing the commands below

```bash
dnf update -y && dnf upgrade -y

dnf clean all

reboot
```
![[Pasted image 20250517053101.png]]

**Step 2:** Installation of Java Development Kit (JDK)
```bash
cd /opt

wget https://download.oracle.com/java/21/latest/jdk-21_linux-x64_bin.rpm

rpm -Uvh jdk-21_linux-x64_bin.rpm

java -version

cd /

clear
```

Time to see if the installation was successful:
![[Pasted image 20250517054626.png]]

**Step 3:** Install Elasticsearch in RHEL.

**I.** Import the Elasticsearch public GPG key into the RPM package manager.
```bash
rpm--import https://artifacts.elastic.co/GPG-KEY-elasticsearch
```
![[Pasted image 20250517054942.png]]

**II.** Create the repository configuration file elasticsearch.repo, add the following lines:

nano /etc/yum.repos.d/elasticsearch.repo
```bash
[elasticsearch]
name=Elasticsearch repository for 9.x packages
baseurl=https://artifacts.elastic.co/packages/9.x/yum
gpgcheck=1
gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
enabed=0
autorefresh=1
type=rpm-md
```
![[Pasted image 20250517055332.png]]

**III.** Update to the latest packages to the latest version. Get and install the Elasticsearch package.
```bash
dnf update -y && dnf makecache
dnf install --enablerepo=elasticsearch elasticsearch -y
```
![[Pasted image 20250517055945.png]]

**Note:** When the installation is completed, you will be need to copy and keep the credentials for the superuser under autoconfiguration information section of the installation output shown from the line below
```bash
The generated password for the elastic built-in superuser is : zZzct2F8E-7TrKNW_24I
```

**IV.** Confirm the package installation.
```bash
rpm -qi elasticsearch
```
![[Pasted image 20250517060151.png]]

**V.** Allow remote access by specific the IP or IP Range as shown below
```bash
nano /etc/elasticsearch/elasticsearch.yml
```

Uncomment and edit the lines as shown below or leave the commented lines and make new entry as shown below
```bash
network.host: 0.0.0.0  
http.port: 9200  
node.name: elasticsearch-dbiz-monitor 
# Single Node Discovery  
discovery.seed_hosts: ["single-node"]
transport.host: 0.0.0.0
```
![[Pasted image 20250517060805.png]]
![[Pasted image 20250517060904.png]]
![[Pasted image 20250517060922.png]]

**VI.** Launch and enable the service.
```bash
systemctl daemon-reload  
systemctl enable elasticsearch  
systemctl start elasticsearch  
systemctl status elasticsearch
```
![[Pasted image 20250517062327.png]]

**VII.** Allow traffic over TCP port 9200 in your firewall.
```bash
firewall-cmd --add-port=9200/tcp

firewall-cmd --zone=public --permanent --add-port=9200/tcp

firewall-cmd --reload
```
![[Pasted image 20250517062518.png]]
**VIII.** Type on the browser, you will get a login page

##### **How to configure send metrics postgresql to elasticsearch with metricbeat module (postgresql.yml)**

**Note:** case study and command for this project

**Link reference:**
	-  [PostgreSQL module cannot connect](https://discuss.elastic.co/t/postgresql-module-cannot-connect/220916)
	-  [Postgresql module](https://www.elastic.co/docs/reference/beats/metricbeat/metricbeat-module-postgresql)

- enable postgre in metricbeat 
```bash
sudo metricbeat modules enable postgresql
sudo metricbeat modules disable system
```

- restart metricbeat
```bash
sudo systemctl status metricbeat -l
sudo systemctl restart metricbeat
```

- login postgresql with port change
```bash
psql -U postgres -p 51173 "login with port 51173 default port 5432"

\q "exit login postgresql"

```

- check permission on database postgresql **(alredy login superuser)**
```bash
\dp pg_stat_activity "check on ACTIVITY "

\dp pg_stat_database "check on DATABASE "

\dp pg_stat_bgwriter "check on BGWRITER "
```

- check database already create in postgresql
```bash
SELECT datname FROM pg_database WHERE datistemplate = false; "database"
```

- check port open 
```bash
netstat -tulnp
```

- test configure
```bash
sudo metricbeat test config
```

- check version postgresql
```bash
postgres --version
```

- allow port on firewall oracle linux server
```bash
sudo firewall-cmd --add-port=5432/tcp --permanent

sudo firewall-cmd --add-port=51173/tcp --permanent

sudo firewall-cmd --reload

sudo firewall-cmd --list-all

sudo firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="172.16.3.12/24" port port="5432" protocol="tcp" accept'

sudo firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="172.16.3.12/24" port port="51173" protocol="tcp" accept'
```

###### **Step by step configure**

**I.**  Enable metricbeat postgresql module on vm running postgresql.

```bash
sudo metricbeat modules enable postgresql
```
![[Pasted image 20250519045735.png]]

**II.**  Configure information necessary for connect among metricbeat->postgresql->elasticsearch.

```bash
- module: postgresql

metricsets:

- database

- bgwriter

- activity

- statement

period: 10s

hosts: ["postgres://172.16.3.12:51173?sslmode=disable"]

username: postgres

password: HrWL(f#vXnrIWNkL
```
![[Pasted image 20250519045459.png]]

**III.**  