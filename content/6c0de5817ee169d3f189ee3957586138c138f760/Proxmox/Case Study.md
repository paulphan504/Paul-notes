Allway setup static ip address for VM and setup network card follow with image ![[Pasted image 20241124233235.png]]

[Create folder for mount extend hdd or usb for copy data direct form usb to proxmox server](https://thehomelab.wiki/books/promox-ve/page/add-external-usb-storage-to-proxmox)

**Figure out what drive it is**:

Find the drive device ID running this command
```bash
fdisk -l
```
**Create folder for mounting**:

Now we have to make a folder where the drive will be mounted. I used the following folder.
```bash
mkdir /mnt/USB_Data
```
Now we mount the drive to it
```bash
mount /dev/sdb1 /mnt/USB_Data
```

[How to install 7zip to extract zip/rar file](https://askubuntu.com/questions/348173/how-to-install-7zip-to-extract-rar-files)
To unrar files with... 7zip: 
```bash
sudo apt-get install p7zip-full
7z x some.rar
```
and `x` mean extract obviously.

[How to install extension copy&paste for Proxmox VE console](https://gist.github.com/amunchet/4cfaf0274f3d238946f9f8f94fa9ee02)

1. Install Tampermonkey for your browser ([https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo?hl=en](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo?hl=en))
2. Open up this script in "Raw" (or go to this url: [https://gist.github.com/amunchet/4cfaf0274f3d238946f9f8f94fa9ee02/raw/0b84970f89e1f282f09b86d46227eda71178c040/noVNCCopyPasteProxmox.user.js](https://gist.github.com/amunchet/4cfaf0274f3d238946f9f8f94fa9ee02/raw/0b84970f89e1f282f09b86d46227eda71178c040/noVNCCopyPasteProxmox.user.js))
3. Click install
4. [Optional] if you have a non-US keyboard layout, you may need to modify the script.
5. Copy some text to your clipboard (highlight some text and Ctrl + C)
6. Open up your Promox console
7. Right click to paste the text into the console (you may need to restart your browser, depending on your tampermonkey installation)

Note: if you use LXC containers, you do not need this script, as you can just copy and paste normally from that terminal.

If you have any other questions, please feel free to ask!

[How to import file .OVA to Proxmox VE server](https://www.vinchin.com/vm-backup/proxmox-import-ova-ovf.html)

[Extend Boot Drive Storage In Proxmox (Resize)](https://www.youtube.com/watch?v=SsOLRiN4l9c)
Refer comand script and solution other with many systems: [link](https://github.com/webmentordev/linux-bash-scripts-and-solutions/blob/master/Extend%20Proxmox%20Storage.txt)

[How to copy source with SCP protocal](https://www.veerotech.net/kb/how-to-use-secure-copy-protocolscp-to-transfer-files-securely-on-linux-and-mac/)
**Quick Steps**

1. 1. Open a terminal window.
    2. Upload files to your VeeroTech Hosting account with this command
        
        **scp -P 22 filename _username@example.com_:~/destination**
        
    3. Enter your password.
    4. Download files from your VeeroTech Hosting account with this command
        
        **scp -P 22 _username@example.com_:~/file destination**
        
    5. Enter your password when prompted, and SCP will download the file to the specified destination directory.

**Fix error when install windows 11 on proxmox: need chosses CPU Processors 2 or more than**
![[Pasted image 20241129124248.png]]