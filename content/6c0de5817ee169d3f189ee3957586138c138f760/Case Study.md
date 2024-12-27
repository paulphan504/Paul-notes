- **Wireshare**: Test flow packet data running when connect vpn Wireguard Tunnel use dns Adgurad on local macbook (127.0.0.1 / 172.16.18.81)
	- Full traffic data via vpn
	- Slipt traffic data via vpn

- Install Adgurad on Docker 
```bash
sudo docker run --name adguardhome\
    --restart unless-stopped\
    -v /my/own/workdir:/opt/adguardhome/work\
    -v /my/own/confdir:/opt/adguardhome/conf\
    -p 54:53/tcp -p 54:53/udp\
    -p 67:67/udp -p 68:68/udp\
    -p 82:80/tcp -p 444:443/tcp -p 444:443/udp -p 3002:3000/tcp\
    -p 853:853/tcp\
    -p 784:784/udp -p 853:853/udp -p 8853:8853/udp\
    -p 5443:5443/tcp -p 5443:5443/udp\
    -d adguard/adguardhome

```