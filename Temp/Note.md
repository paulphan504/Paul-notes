- **[Open link safe](https://youtube.com/shorts/ElQxbbNBayI?si=SYOIFyCQ8Y9axI7o)**

```
wget https://github.com/prometheus/node_exporter/releases/download/v1.8.2/node_exporter-1.8.2.linux-amd64.tar.gz
[prometheus-2.55.0-rc.0.linux-amd64.tar.gz](https://github.com/prometheus/prometheus/releases/download/v2.55.0-rc.0/prometheus-2.55.0-rc.0.linux-amd64.tar.gz)
tar xvfz node_exporter-*.*-amd64.tar.gz
cd node_exporter-*.*-amd64
./node_exporter
```

- **[Cartoon energy (The Wild Robot):](https://motchilltc.us/xem/robot-hoang-da-the-wild-robot/full)** [link](https://motchilltc.us/xem/robot-hoang-da-the-wild-robot/full)

- [Orbstack intruduce method for replace Docker Desktop](https://www.youtube.com/watch?v=aJe7CvQ-aM8)

- [VScode intruduce](https://www.youtube.com/watch?v=1ZfO149BJvg&t=208s)

- [Intruduce youself trainer by youtuber Lucy](https://www.youtube.com/watch?v=QgjkjsqAzvo)

- [improve lisening english skill native](https://youtube.com/watch?v=D6_qpaSxAQc&si=x7c1gERtsJ7j5B96 )
  
- Pi-Hole vs Adguard

- PFSence https://youtube.com/watch?v=lUzSsX4T4WQ&si=uFU0_d0-VQN4MRJK


- Zabbix
- [ ] go to home (@2024-11-30)
- [ ] Relax (@2024-11-30)

docker run -d \
--name=ubuntu \
--security-opt seccomp=unconfined \
-e PUID=1000 \
-e PGID=1000 \
-e TZ=Etc/UTC \
--restart unless-stopped \
ubuntu:latest
- [ ] Practice mounth and void sound(@2024-11-30) [link](https://www.youtube.com/watch?v=l69yZ5xabbo&t=3s)

# Minimal command
docker run -d --name pihole --network=host -e WEBPASSWORD="YourPassword" -e DNS1=1.1.1.1 -p 80:80 -p 53:53/tcp -p 53:53/udp -p 443:443 pihole/pihole:latest

# Recommended command
docker run -d --name pihole -e ServerIP=172.16.18.86 -e TZ=Europe/Helsinki -e WEBPASSWORD=SecretAgent007 -e DNS1=1.1.1.1 -e DNS2=1.0.0.1 -p 80:80 -p 53:53/tcp -p 53:53/udp -p 443:443 -v ~/pihole/:/etc/pihole/ --dns=127.0.0.1 --dns=1.1.1.1 --cap-add=NET_ADMIN --restart=unless-stopped pihole/pihole:latest

marker_single -h --batch_multiplier 2 --max_pages 10 Tiêu Chuẩn An Toàn Thông Tin /CATTT_CAM NANG RANSOMWARE.pdf Slides
marker_single /Users/ptp/Desktop/1/1.pdf /Users/ptp/Desktop/2 --batch_multiplier 2 --max_pages 10 --langs English
.


<<<<<<< HEAD
App on macbook
![[Pasted image 20241124093212.png]]
![[Pasted image 20241124093233.png]]
![[Pasted image 20241124093257.png]]

**config login asdm on asa temp:** 
ASDM - gui tool

show run in http
aaa authentication http console LOCAL
http server enable
http 192.168.159.0 255.255.255.0 inside
webvpn <mark style="background: #FFF3A3A6;">"maybe unnecssary"</mark>
username ahsan password xxXxX



<mark style="background: #FF5582A6;">**How to fix full disk on vm windows 11 (wm not start screen login )**</mark>

[<mark style="background: #FF5582A6;">**Clientless funtion on asa can for client connect to internet when access vpn on web vnp**</mark>](https://www.networkgalaxy.org/2013/06/clientless-ssl-vpn-webvpn-configuration.html?m=1)

1. Config NAT interface ASA outsite <mark style="background: #FFF3A3A6;">on router ISP</mark> [link](https://networklessons.com/cisco/asa-firewall/cisco-asa-anyconnect-remote-access-vpn) [link2](https://www.networkstraining.com/cisco-asa-firewall-with-pppoe/) [link3](https://networkengineering.stackexchange.com/questions/41959/vpn-ipsec-tunnel-between-private-ip-asa-public-ip-asa) [link4](https://www.cisco.com/c/en/us/support/docs/security/ios-easy-vpn/200307-Configure-Easy-VPN-Tunnel-Between-Router.html) [link5](https://www.cisco.com/c/en/us/support/docs/ip/network-address-translation-nat/13778-9.html)
2. Config Bridge mode on route isp and pppoe on interface vlan asa device [link](https://www.expertnetworkconsultant.com/expert-approach-in-successfully-networking-devices/configure-cisco-asa-5506-x-for-pppoe-passthrough/)


