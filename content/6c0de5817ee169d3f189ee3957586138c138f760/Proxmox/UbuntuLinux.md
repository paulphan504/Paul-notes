#####  **Ubuntu desktop Information:**

| **Username:**     | paullinuxdesktop@paullinuxdesktop-Standard-PC-i440FX-PIIX-1996 |
| ----------------- | -------------------------------------------------------------- |
| **IP:**           | 172.16.18.90/27                                                |
| **Network Name:** | ens19                                                          |
| **Status:**       | Static ip address setup on file  with information below<br>    |
| DNS               | 1.1.1.1                                                        |

- Directory content file
```bash
cd /etc/netplan/
sudo nano 01-network-manager-all.yaml
```

- **Configure file information:**
![[Screenshot 2024-12-09 at 09.07.14.png]]
       
- ##### Connect remote thought Teamviewer 
```bash
id: 1072 505 988
Pass: 
```

- ##### **Connect remote thought Anydesk**
```bash
id: 1 343 214 487
pass: 
```

- ##### **How to connect Ubuntu Desktop thought teamviewer + anydesk**

<mark style="background: #FF5582A6;">*Note:* <mark style="background: #FF5582A6;">no clock Ubuntu Desktop vm</mark>  only restart, logout if you want connect again with temviewer.</mark>

- connect teamviewer with id and password below 
	- login password on ubuntu desktop
	- open anydesk
- connect anydesk with id and password below 
	- accept connecting for anydesk (login form outsite devices to ubuntu desktop vm on proxmox)
	- <mark style="background: #FFF3A3A6;">close connection teamview on outside devices</mark>

##### **How to shutdown Proxmox server thought remote anydesk from Ubuntu Desktop vm on proxmox** 
- open shell from website manage proxmox vm type comman
```bash
sudo shutdown now
```
- shutdown ubuntu desktop
```bash
sudo shutdown now
```
- close anydesk remote to ubuntu desktop.

------------------------------------------------------------------------

[How to add new device network card and put ip address on ubuntu server](https://ubuntu.com/server/docs/configuring-networks)

- add new network card on vm ubuntu server on proxmox vm
![[Pasted image 20241203222347.png]]

- add ip static for network card
```bash
sudo ip addr add 172.16.18.90/27 dev ens19
```
- apply setup on network card
```bash
sudo netplan apply
```

- show information interface network card
```bash
ip a
```
- turn on network card running on ubuntu server 
```bash
sudo ip link set dev ens19 up
```
- add route gateway for network card
```bash
sudo ip route add default via 172.16.18.68 dev ens19
```
- show ip information specify interface network
```bash
ip addr show dev ens19
```
- refresh dns for network card
```bash
sudo ip addr flush ens19
```
- show ip route
```bash
ip route show
```

How to install and enable ssh server on Ubuntu
```bash
sudo apt install openssh-server
sudo systemctl status ssh
sudo ufw allow ssh 'if have configure firewall in system'
```

##### **Ubuntu Server Information:**

| **Username:**     | paul@linuxserver |
| ----------------- | ---------------- |
| **IP:**           | 172.16.18.92     |
| **Network Name:** | ens18            |
| **DNS:**          | 1.1.1.1<br>      |
##### **[How to setup static ip on ubuntu server with file config](https://krishnendubhowmick.medium.com/how-to-configure-a-static-ip-address-on-ubuntu-20-04-22-04-lts-step-by-step-4a35d6662083)**

1. Copy file config for backup.
```bash
paul@linuxserver:~$ sudo cp /etc/netplan/50-cloud-init.yaml /etc/netplan/50-cloud-init.yaml.copy
```
 2. Edit Netplan configuration.
 ```bash
 paul@linuxserver:~$ sudo nano /etc/netplan/50-cloud-init.yaml
```
![[Screenshot 2024-12-09 at 09.00.27.png]]
3. Apply new ip address
```bash
paul@linuxserver:~$ sudo netplan apply
```
4. Add dns server to file config 

`paul@linuxserver:~$ sudo rm /etc/resolv.conf`

`paul@linuxserver:~$ sudo nano /etc/resolv.conf`

```bash
paul@linuxserver:~$ nameserver 1.1.1.1 'add dns server to file resolv.conf'
```

##### **[How to find one file on linux ubuntu](https://www.tutorialrepublic.com/faq/how-to-find-a-file-by-name-using-command-line-in-ubuntu.php)**

```bash
find /path/to/directory -type f -name filename.ext
```

*ex:* For example, to find the file named "sample.txt" within the `/var/www` you can use:

`find /var/www -type f -name sample.txt `

##### **How to show version with comman**
```bash
sudo lsb_release -a
```

[How to show port open and configure firewall on Ubuntu Server ](https://linuxconfig.org/how-to-check-for-open-ports-on-ubuntu-linux)

```bash
sudo ss -ltnp "show port and services open on ubuntu server with command ss"
sudo nmap localhost "show port and services open on ubuntu server with command nmap"
sudo ufw status verbose "show status action off fw on ubuntu server"
sudo ufw allow 80/tcp "permit port 80/tcp access via fw"
```