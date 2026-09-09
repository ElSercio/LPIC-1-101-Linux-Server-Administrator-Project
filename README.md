# LPIC-1-101-Linux-Server-Administrator-Project
This project demonstrates the skills obtained from a preparation course to achive LPIC-1Certification. The server was created using Azure and ubuntu server 24-04.

Phase 1
-Launched the Virtual Machine on Azure and established a remote connection using the command "ssh -i" from my personal laptop.
-Created a file named "hardware_info.txt" using the commands lspcu, free and fdisk and pipes in order to obtain CPU, RAM and Storage information.

Phase 2
- In this project is being used an Ubuntu Server, so there is no need to have a graphical.target unit as the default target.
- Therefore I changed the default target from graphical.target to multi-user.target with the command "systemctl set-default multi-user.target
- In addition, I setup a password for the user sagsadmin with the command sudo passwd sagsadmin.
