##### Connect remote thought Teamviewer 
```bash
id: 536 994 593
Pass: Ptp@#2024
```

##### **Connect remote thought Anydesk**
```bash
id: 1 343 214 487
pass: 
```

##### **How to connect Ubuntu Desktop thought teamviewer + anydesk**
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


