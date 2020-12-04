---
title: "Hardening Ubuntu"
categories:
  - Ubuntu
  - ufw
---

This is a short list, largely borrowed from [digitalocean](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-20-04)

1. Log in with your provided root credentials

   > ssh root@123.123.123.123

2. Create a user (just hit enter and skip the info if you want)

   > adduser username

3. Enable the user to use sudo

   > usermod -aG sudo username

4. Disable root SSH login

   > nano /etc/ssh/sshd_config

   Modify the file like below. Pick a high port number between 1024 and 34627. Hit ctrl-x, 'Y' and finally hit enter to save.

   > ~~PermitRootLogin yes~~ PermitRootLogin no  
   > ~~#Port 22~~ Port 12345

   Finally reboot and log in with the new settings

   > reboot  
   > ssh username@123.123.123.123 -p 12345

   From now on we might need to use 'sudo' to run certain commands.

5. Enable the ufw firewall. Check digital oceans [guide](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-18-04) for more details

   > sudo ufw allow 12345  
   > sudo ufw default deny incoming  
   > sudo ufw default allow outgoing  
   > sudo ufw enable  
   > sudo ufw status

   Lets reboot and check if everything is working with 'sudo reboot'

6. See here for more ufw commands, but in short they are:

   > sudo ufw deny  
   > sudo ufw status numbered  
   > sudo ufw delete 2  
   > sudo ufw delete allow OpenSSH  
   > sudo ufw status verbose  
   > sudo ufw reset

7. Update
   > sudo apt-get update  
   > sudo apt-get upgrade  
   > sudo apt-get dist-upgrade
