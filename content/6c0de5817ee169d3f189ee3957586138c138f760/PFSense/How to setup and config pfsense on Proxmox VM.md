
| Web page communication     | [link](https://www.reddit.com/r/PFSENSE/comments/1co8f1o/pfsense_iso_download_requires_an_account_and/) |
| -------------------------- | ------------------------------------------------------------------------------------------------------- |
| Download source:           | [link](https://repo.ialab.dsu.edu/pfsense/)                                                             |
| Video training             | [link](https://www.youtube.com/watch?v=mwDv790YoZ0)                                                     |
| Devices Name on proxmox vm | pfsense                                                                                                 |
| IP Wan                     | 172.16.18.94 /27                                                                                        |
| IP Lan                     | 192.168.1.1 /24                                                                                         |
<mark style="background: #FFF3A3A6;">Note: Lan card on pfsense proxmox vm (**enp4s0** create Linux Bridge **vmbr1**) can connect direct to external pc/laptop/sw recived dhcp client provide form pfsense</mark>

****
![[Pasted image 20241221221345.png]]

setup hardware for pfsense
![[Pasted image 20241221214011.png]]


##### **How to connect pfsense with ip wan on lab local** 

**note:** with **Lan** setup similar step by step  

On top off main pages choose **Interfaces** croll down the end off pages unstick two options (**Block private networks and loopback addresses** and **Block bogon networks**)

![[Pasted image 20241221223713.png]]

Create rules permit protocol via **Wan** interface
![[Pasted image 20241221223740.png]]


##### **How to configure https, ssh login on pfsense**

![[Screenshot 2024-12-21 at 22.44.35.png]]![[Pasted image 20241221224727.png]]

##### **[How to configure dns resolver](https://172.16.18.94/services_unbound.php)** 

Note: default already on for this function on fw, you can disable or use access lists deny/permit for network you expect
![[content/6c0de5817ee169d3f189ee3957586138c138f760/PFSense/images/Screenshot 2024-12-23 at 12.19.13.png]]
![[Pasted image 20241223122746.png]]