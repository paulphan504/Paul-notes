#####  **[To remove the UniFi Controller software from a Mac completly:](https://community.ui.com/questions/How-do-I-completely-remove-Unifi-Software-from-Mac-to-start-a-brand-new-network/e10c1fbd-e6b2-48ed-aae3-f874e8869961)**

1. backup the UniFi Controller
2. delete the UniFi app
3. delete the folder: ~/Library/Application\ Support/UniFi/ "<mark style="background: #FFF3A3A6;">command + shift+g</mark> and paste path for open"
4. Install the UniFi app again

##### **[How to install unifi controller on Docker with compose file via Ubuntu Server 22.04 via Proxmox VM ](https://pimylifeup.com/unifi-docker/)**

![[Pasted image 20241223231945.png]]

- Compose file
  ```bash
  services:
  unifi:
    user: unifi
    image: ghcr.io/jacobalberty/unifi-docker
    container_name: unifi-controller
    restart: unless-stopped
    ports:
      - "8080:8080"
      - "8443:8443"
      - "3478:3478/udp"
      - "10001:10001/udp"
    environment:
      TZ: "<TIMEZONE>"
    volumes:
      - ./data:/unifi
```

![[Screenshot 2024-12-23 at 23.22.14.png]]