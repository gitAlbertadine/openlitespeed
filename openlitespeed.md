## Initial setup/\
```
passwd
adduser said
passwd said
gpasswd -a said wheel
rsync --archive --chown=$USER:$USER ~/.ssh /home/said
chown -R said:said /home/said/.ssh
yum check-update
yum update
yum install python2 python3 -y
fallocate -l 1G /swapfile
dd if=/dev/zero of=/swapfile bs=1024 count=1048576
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile
sh -c 'echo "/swapfile none swap sw 0 0" >> /etc/fstab'
timedatectl set-timezone America/New_York
systemctl restart chronyd
#cat /proc/swaps
#timedatectl
#python2 --version
#python3 --version
```
## firewalld/\
```
yum install -y firewalld firewall-config firewall-applet
systemctl start firewalld
systemctl unmask --now firewalld.service
firewall-cmd --permanent --add-service=ssh --zone=public
firewall-cmd --permanent --add-service=http
firewall-cmd --permanent --add-service=https
#firewall-cmd --permanent --zone=public --add-port=8090/tcp
firewall-cmd --permanent --zone=public --add-port=7080/tcp
firewall-cmd --permanent --zone=public --add-port=9090/tcp
firewall-cmd --permanent --zone=public --add-port=80/tcp
firewall-cmd --permanent --zone=public --add-port=443/tcp
firewall-cmd --permanent --zone=public --add-port=443/udp
#firewall-cmd --permanent --zone=public --add-port=21/tcp
#firewall-cmd --permanent --zone=public --add-port=40110-40210/tcp
#firewall-cmd --permanent --zone=public --add-port=25/tcp
#firewall-cmd --permanent --zone=public --add-port=587/tcp
#firewall-cmd --permanent --zone=public --add-port=465/tcp
#firewall-cmd --permanent --zone=public --add-port=110/tcp
#firewall-cmd --permanent --zone=public --add-port=143/tcp
#firewall-cmd --permanent --zone=public --add-port=993/tcp
#firewall-cmd --permanent --zone=public --add-port=53/tcp
#firewall-cmd --permanent --zone=public --add-port=53/udp
firewall-cmd --reload
systemctl enable --now firewalld.service
#firewall-cmd --permanent --list-all
#sudo firewall-cmd --permanent --remove-service=ssh
#sudo firewall-cmd --get-services
#-visit: webadmin consol
#https:<IP Address>:7080
#-setup and login to OpenLiteSpeed webadmin console(change password)
#/usr/local/lsws/admin/misc/admpass.sh
#-visit cockpit
#https:<IP Address>:9090

```
## root/\
```
[#vi /etc/ssh/sshd_config
#PermitRootLogin no
#systemctl reload sshd]
```
## chrony/\
```
[timedatectl set-timezone America/New_York
#timedatectl
yum install -y chrony
systemctl start chronyd
systemctl enable chronyd
systemctl restart chronyd]
```
## epel-release/\
```
yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
yum update
#rpm -qa | grep epel
#yum repolist
```
## remi-release/\
```
yum install -y https://rpms.remirepo.net/enterprise/remi-release-8.rpm
#yum repolist
```


## openlitespeed/\
```
rpm -Uvh http://rpms.litespeedtech.com/centos/litespeed-repo-1.1-1.el8.noarch.rpm
#yum repolist
yum install -y openlitespeed
systemctl start lsws
systemctl enable lsws
yum install -y lsphp74 
yum install -y lsphp74-*
ln -sf /usr/local/lsws/lsphp74/bin/lsphp /usr/local/lsws/fcgi-bin/lsphp5
#netstat -pl | grep lsphp

```
## MariaDB/\
```
yum -y upgrade
tee /etc/yum.repos.d/MariaDB.repo<<EOF 
[mariadb]
name = MariaDB
baseurl = http://yum.mariadb.org/10.4/centos8-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
EOF
yum install -y boost-program-options
yum install -y MariaDB-server MariaDB-client --disablerepo=AppStream      [yum remove mariadb mariadb-server// rm -rf /var/lib/mysql// rm /etc/my.cnf]
systemctl enable --now mariadb
mysql_secure_installation
mysql -u root -p
MariaDB [(none)]> select User, Password, Host from mysql.user;
#Admin Password Authentication/\
```
## Configure OpenLiteSpeed with PHP 7.4/\
```
#Server Configuration>External App>+ LiteSpeed SAPI App>next
#-add:
-Name: lsphp74
-Address: uds://tmp/lshttpd/lsphp.sock
-Notes: lsphp74 for OpenLiteSpeed
-Max Connections: 35
-Initial Request Timeout (secs): 60
-Retry Timeout (secs): 0
-Command: $SERVER_ROOT/lsphp74/bin/lsphp
#Listener>Default>view>Address Settings>edit>80>save
# Testing http://IP
```
## Wordpress/\
```
-mysql -u root -p
-mariadb> CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
-mariadb> GRANT ALL ON wordpress.* TO 'adam'@'localhost' IDENTIFIED BY 'Ax<x3$*>xB';
-mariadb> FLUSH PRIVILEGES;
-mariadb> SELECT user,authentication_string,plugin,host FROM mysql.user;
-mariadb> show databases;
-mariadb> exit
yum install -y wget unzip && cd /usr/local/lsws/Example/html && wget https://wordpress.org/latest.zip && unzip latest.zip && rm latest.zip
chown -R nobody:nobody /usr/local/lsws/Example/html/wordpres
```
