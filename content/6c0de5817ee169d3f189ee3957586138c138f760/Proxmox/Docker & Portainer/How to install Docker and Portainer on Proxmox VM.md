**Summary:**

Refer link setup: https://www.youtube.com/watch?v=wrlukx-QYRw&t=10s

- VM Ubuntu server install on proxmox vm [[UbuntuLinuxServer]]
	- enable ssh on ubuntu server, advantage for copy and paste command form internet for setup
- Install docker on ubuntu server [link](https://docs.docker.com/engine/install/ubuntu/) 
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
```
- Install portainer on ubuntu server [link](https://docs.portainer.io/start/install-ce/server/docker/linux)
```bash
docker volume create portainer_data

docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:2.21.4
```
- Connect to portainer with web browser https://172.16.18.90:9443 and create user name and password for begin login to manage page