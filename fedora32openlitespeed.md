## fedora openlitespeed 
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
firewall-cmd --permanent --add-service=ssh --zone=public
firewall-cmd --permanent --zone=public --add-port=7080/tcp
firewall-cmd --permanent --zone=public --add-port=8088/tcp
firewall-cmd --permanent --zone=public --add-port=9090/tcp
firewall-cmd --permanent --zone=public --add-port=80/tcp
firewall-cmd --permanent --zone=public --add-port=443/tcp
firewall-cmd --permanent --zone=public --add-port=443/udp
firewall-cmd --reload
systemctl enable --now firewalld.service
dnf install libnsl -y
wget https://openlitespeed.org/packages/openlitespeed-1.6.12.tgz
tar -zxvf openlitespeed-1.6.12.tgz
cd openlitespeed
./install.sh
/usr/local/lsws/bin/lswsctrl start
/usr/local/lsws/bin/lswsctrl status
#http://localhost:8088/
/usr/local/lsws/admin/misc/admpass.sh
#-PHP
dnf -y install https://rpms.remirepo.net/fedora/remi-release-32.rpm
dnf config-manager --set-enabled remi
dnf config-manager --set-enabled remi-php74
dnf config-manager --set-disabled remi-modular
dnf install php
dnf install php-litespeed php-mysqlnd php-gd php-mcrypt php-bcmath php-zip php-devel php-curl php-pear
php -v

[
Name: lsphp74
Address: uds://tmp/lshttpd/lsphp.sock
Max Connections: 40
Environment: PHP_LSAPI_MAX_REQUESTS=500
PHP_LSAPI_CHILDREN=40
LSAPI_AVOID_FORK=200M
Initial Request Timeout (secs): 60
Retry Timeout : 0
Persistent Connection: Yes
Response Buffering: no
Start By Server: Yes(Through CGI Daemon)
Command: /usr/bin/lsphp
Back Log: 100
Instances: 1
Priority: 0
Memory Soft Limit (bytes): 2047M
Memory Hard Limit (bytes): 2047M
Process Soft Limit: 1400
Process Hard Limit: 1500
] 
install mysql........
```
