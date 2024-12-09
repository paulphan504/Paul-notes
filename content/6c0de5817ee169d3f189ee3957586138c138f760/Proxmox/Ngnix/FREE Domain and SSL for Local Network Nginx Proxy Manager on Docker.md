Refer link setup: https://www.youtube.com/watch?v=acturgE4TmE&t=36s
- Free domain for local Duck DNS [link](https://www.duckdns.org/domains)
- Source for NGNIX Server Manager [link](https://hub.docker.com/r/jc21/nginx-proxy-manager)

veth807b6bf
network:
ethernets:
veth807b6bf
dhcp4: false
addresses: [172.16.18.92/27]
routes:
to: default
via: 172.16.18.68
nameservers:
addresses: [172.16.18.81]