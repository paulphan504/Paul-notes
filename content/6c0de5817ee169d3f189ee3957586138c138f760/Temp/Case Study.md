##### 1. **Wireshare: Test flow packet data running when connect vpn Wireguard Tunnel use dns Adgurad on local macbook (127.0.0.1 / 172.16.18.81)**
	- Full traffic data via vpn
	- Slipt traffic data via vpn "local traffic access thought vpn Wiregurad, internet traffic access thought dns setup on devices provide maybe form modem/dns_services(adgurad local, 1.1.1.1, 8.8.8.8)"

##### 2. Install Adgurad on Docker 
```bash
sudo docker run --name adguardhome\
    --restart unless-stopped\
    -v /my/own/workdir:/opt/adguardhome/work\
    -v /my/own/confdir:/opt/adguardhome/conf\
    -p 54:53/tcp -p 54:53/udp\
    -p 67:67/udp -p 68:68/udp\
    -p 83:80/tcp -p 445:443/tcp -p 445:443/udp -p 3000:3000/tcp\
    -p 853:853/tcp\
    -p 784:784/udp -p 853:853/udp -p 8853:8853/udp\
    -p 5443:5443/tcp -p 5443:5443/udp\
    -d adguard/adguardhome

```

2. 1/ Connect to web configure Adgurad but not have information  **username/password** login
   <mark style="background: #BBFABBA6;">Resolve:</mark> [how to change password adgurad install on container/ubuntuserver/proxmox](https://hostingcanada.org/htpasswd-generator/)
   - You need to edit the password field in the `AdGuardHome.yaml` file. Use this to generate a new password (you must set it to `BCrypt`): [https://hostingcanada.org/htpasswd-generator/](https://hostingcanada.org/htpasswd-generator/)
   ![[Pasted image 20241230171805.png]]
   Login console of container running Adguradhome, type command 
   ```bash
		su - "login root account"
		cd /
		cd /opt/adguradhome/conf/
		vi Adguradhome.yml
		Paste password hash to file .yml
		i "login write mode in vi"
		esc "exit write in vi"
		:w "save file"
		:q "exit vi"
	```
   ![[Pasted image 20241230171953.png]]
	![[Pasted image 20241230172710.png]]
   
2. 2/ Install new container run web browser **chrome/fire_fox/brave_browser** with same network card Bridge
   2.2.1/ Login Adgruad with **ip card bridge** with port **3000 or 3002** same with configure yml file
##### 3. **Setup KASM_Server  serves for open container running web_browser install on step 2.2**
3. 1/ How to ssh to container install KASM_Server , because when connect direct via Portainer/Container Console disadvangeted 
		<mark style="background: #BBFABBA6;">***Resolve:*** connect ssh to container [[How to install Docker and Portainer on Proxmox VM]]</mark>

##### 4. **How to Fix connect container/ubuntuserver/promoxvm with port manual ssh 222  with explain in image below.** 
![[Pasted image 20241227233528.png]]

<mark style="background: #BBFABBA6;">**Resolve:**</mark> create port manual you expect for container (ex:2222), implementation install openssh_server and step by step follow guide [[$ Comman in terminal macos & linux.]] with key word <mark style="background: #FFF3A3A6;">How to Install and Enable SSH with Password Authentication on Ubuntu</mark>

![[Pasted image 20241230155303.png]]

- Login ssh with port manual (ex:2222) on VS Code
![[Pasted image 20241230161339.png]]
##### 5. **How to connect and apply DHCP_server/Vlan form network of Router/SW in Eve-ng environment to Devices/VM on Proxmox VM**
<mark style="background: #BBFABBA6;">Resolve: 
 Provide dhcp form Router on Eve-ng to vm on Proxmox (network card Bridge Cloud2/pnet2/eth2/vmbr2) and vm windows 10 on Eve-ng (network card Cloud2/pnet2/eth2/vmbr2)</mark>
![[Pasted image 20241228172104.png]]
- Command configure on Router R7
```bash

```

##### 6. **[How to ssh to router on eve-ng with teminal macos](https://gulian.uk/8-steps-to-configure-ssh-on-a-cisco-router-or-switch/)**
- **Note:** 
	- Only connect vpn Wiregurad on vlan 20/40/1 for ssh to router with diagram above 
	![[Pasted image 20241228223025.png]]
	- <mark style="background: #FFF3A3A6;">VS Code not connect ssh to router (thought can access to step authenticator)</mark> ![[Pasted image 20241228223509.png]]
```bash
Router(config) enable secret cisco123 "create password for login Privileged mode"
Router(config) username root secret Ptp@#2024 "create ussername and passoword authenticator thought ssh client"
Router(config) line vty ? "show information of vty"
Router(config-line) line vty 0 4 "setup vty 0 4"
Router(config-line) login local "permit login ssh to local devices(router/sw)" 
Router(config-line) Transport ? "show option transport command"
Router(config-line) Transport input ? "show option input command"
Router(config) Transport input ssh "only us ssh"
Router(config) crypto key generate rsa modulus 1024
Router(config) ip ssh version 2 "choose ssh version"

ssh root@192.168.20.101 -oKexAlgorithms=+diffie-hellman-group14-sha1 -oHostkeyAlgorithms=+ssh-rsa "Test ssh connect with rsa syntax"
```
#####  How to add **ssh Key RSA** to file **know_host**

- RSA key auto create when login ssh to router device.
![[Pasted image 20241228211458.png]]

- Remote ssh to file **~/.ssh/Know_host** in **macos** thought **VS Code**. After type information correct in file **Know_host** press **Command + S** for save and connect again router via ssh client.
```bash
ssh root@192.168.20.101 -oKexAlgorithms=+diffie-hellman-group14-sha1 -oHostkeyAlgorithms=+ssh-rsa
```
![[Pasted image 20241228211323.png]]![[Pasted image 20241228212225.png]]

##### 7. **How to create vlan and add vlan for each devices in network lan**
- devices PaulPhan deny social media (facebook, tiktok, pinterest)
- devices TuyetNguyen deny (tiktok, permit bandwith 20mbps)

##### 8. **How to create pencil write on touchpad mac book PaulPhan with touch gloves**

##### 9. **[How to configure 2FA for GUI access in pfSense](https://www.comparitech.com/blog/vpn-privacy/pfsense-two-factor-authentication/)**
**Resolve:**![[Pasted image 20241230114924.png]]

##### 10. [How to configure Wiregurad on DebianOS and configure client vpn on ios](https://wireguard.how/client/ios/)

- **[Link master clearly:](https://www.zenarmor.com/docs/network-security-tutorials/how-to-install-wireguard-on-freebsd)**
```text
# define the local WireGuard interface (client)
[Interface]

# contents of wg-private-client.key
PrivateKey = oBkgA+KZU6mWY5p7d0PEWxnYkihBw9TmHZXEYnQkz3g=

# the IP address of this client on the WireGuard network
Address=10.0.0.4/32

# define the remote WireGuard interface (server)
[Peer]

# from `sudo wg show wg0 public-key`
PublicKey = zhwUs2tauviw8D4z4SPK17UOfzAcAKa2wfCyWOmmz3w=

# the IP address of the server on the WireGuard network 
AllowedIPs = 10.0.0.1/24

# public IP address and port of the WireGuard server
Endpoint = paulproxmox.duckdns.org:51820
```

```text
# define the remote WireGuard interface (client)
[Peer]

# contents of wg-public-client.key
PublicKey = fAuWUuOxLEk3N6YQF16SPGQKMXQh1PD5KTNRHFPLU0c=

# the IP address of the client on the WireGuard network
AllowedIPs = 10.0.0.4/32
```

<mark style="background: #BBFABBA6;">Resolve: install wiregurad on ubuntu run on container/ubuntuserver OR directive on Proxmox VM</mark>

##### 11. **How to use adgurad on container is proxy for network in container/other network in container/ vm on proxmox**
- how to configure dns on container [link](https://forums.docker.com/t/how-to-config-the-dns-for-a-container/52395)
![[Pasted image 20241230181822.png]]