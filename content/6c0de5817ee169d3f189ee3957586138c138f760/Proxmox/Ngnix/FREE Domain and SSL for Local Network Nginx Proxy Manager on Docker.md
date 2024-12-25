Refer link setup: https://www.youtube.com/watch?v=acturgE4TmE&t=36s
- Free domain for local Duck DNS [link](https://www.duckdns.org/domains)

![[Screenshot 2024-12-09 at 16.25.02.png]]

- Source for NGNIX Server Manager [link](https://hub.docker.com/r/jc21/nginx-proxy-manager)

##### **How to NAT Nginx from local to internet**

<mark style="background: #FFF3A3A6;">**Note:** everything (vm, devices, services) add to host proxy off Nginx can access via internet with domain name respectively.</mark>

- Login website manage Duckdns update information sub domain and ip public internet 
![[Pasted image 20241225102211.png]]

- Nat services port **(81 and 443)** on vm devices running **Nginx Proxy Mannager** (install with patch: Proxmox->UbuntuServer->Docker->Container Nginx Proxy Manager)
![[Pasted image 20241225102655.png]]
![[Pasted image 20241225102614.png]]

- Add **IP address of vm Nginx** and **Appname** already setup up above 
![[Pasted image 20241225103117.png]]

- Access to Nginx vm on web browser, sure everything success
![[Pasted image 20241225103736.png]]