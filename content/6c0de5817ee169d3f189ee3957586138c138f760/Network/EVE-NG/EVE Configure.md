##### [ Set Static IP Address on EVE-NG: Restart the setup process](https://youtube.com/watch?v=rEcYLuaYBGk)
To do this, follow these steps:

1. Login to the EVE-NG VM (default: username: root / password eve)

2. Remove the saved EVE-NG config file: rm -f/opt/of/.configured

3. Restart the setup process: su -

Go through the setup process (select : static IP address using the spacebar)

5. After the reset process is finished, your EVE-NG will be set up with the new static IP address.
##### **How to setup network for virtual devices**

*note:* in this homelab devices connect internet with static ip address example `172.16.18.89 | 255.255.255.224 | GW: 172.16.18.68 | DNS: 172.16.18.81 (my macbook setup Adgurad DNS control all network) `
- bridge: ability connect to internet
- Management(Cloud0): ability ocnnect to internet
![[Pasted image 20241130170157.png]]