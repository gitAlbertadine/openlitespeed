## AIDE
```
dnf install aide
aide --init
cd /var/lib/aide
ls -lt
mv /var/lib/aide/aide.db.new.gz /var/lib/aide/aide.db.gz
aide --check
aide --update
mv aide.db.gz aide.db.gz-Dec082013`
mv aide.db.new.gz aide.db.gz`
```
## Cyberpanel
```
#vi /etc/selinux/config
#-SELINUX=disabled
#sudo reboot
passwd
adduser said
passwd said
gpasswd -a said wheel
rsync --archive --chown=$USER:$USER ~/.ssh /home/said
chown -R said:said /home/said/.ssh
dnf check-update
dnf update
dnf install -y wget  zip unzip  python2 python3 tar
fallocate -l 1G /swapfile
dd if=/dev/zero of=/swapfile bs=1024 count=1048576
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile
sh -c 'echo "/swapfile none swap sw 0 0" >> /etc/fstab'
timedatectl set-timezone America/New_York
systemctl restart chronyd
dnf install -y firewalld firewall-config firewall-applet
systemctl start firewalld
systemctl unmask --now firewalld.service
firewall-cmd --permanent --zone=public --add-port=8090/tcp
firewall-cmd --permanent --zone=public --add-port=7080/tcp
firewall-cmd --permanent --zone=public --add-port=9090/tcp
firewall-cmd --permanent --zone=public --add-port=80/tcp
firewall-cmd --permanent --zone=public --add-port=443/tcp
firewall-cmd --permanent --zone=public --add-port=443/udp
firewall-cmd --permanent --zone=public --add-port=21/tcp
firewall-cmd --permanent --zone=public --add-port=25/tcp
firewall-cmd --permanent --zone=public --add-port=587/tcp
firewall-cmd --permanent --zone=public --add-port=465/tcp
firewall-cmd --permanent --zone=public --add-port=110/tcp
firewall-cmd --permanent --zone=public --add-port=143/tcp
firewall-cmd --permanent --zone=public --add-port=993/tcp
firewall-cmd --permanent --zone=public --add-port=53/tcp
firewall-cmd --permanent --zone=public --add-port=53/udp
firewall-cmd --permanent --zone=public --add-port=40110-40210/tcp
firewall-cmd --reload
firewall-cmd --permanent --list-all
sh <(curl https://cyberpanel.net/install.sh || wget -O - https://cyberpanel.net/install.sh)
#If you want to kill the watchdog , run watchdog kill
#cat /proc/swaps
#timedatectl
#python2 --version
#python3 --version
#firewall-cmd --permanent --list-all
#dnf repolist
-Visit:cyberpanel
https:<IP Address>:8090 
login cyberpanel(change password)
adminPass 'xxxxxxxxxxxxxx'
-visit: webadmin consol
https:<IP Address>:7080
-setup and login to OpenLiteSpeed webadmin console(change password)
/usr/local/lsws/admin/misc/admpass.sh
-visit cockpit
https:<IP Address>:9090
```
