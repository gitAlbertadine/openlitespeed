## Script/\
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
firewall-cmd --permanent --zone=public --add-port=9090/tcp
firewall-cmd --permanent --zone=public --add-port=80/tcp
firewall-cmd --permanent --zone=public --add-port=443/tcp
firewall-cmd --permanent --zone=public --add-port=443/udp
firewall-cmd --reload
systemctl enable --now firewalld.service
dnf install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
dnf update
dnf config-manager --set-enabled PowerTools
dnf install -y https://rpms.remirepo.net/enterprise/remi-release-8.rpm
rpm -Uvh http://rpms.litespeedtech.com/centos/litespeed-repo-1.1-1.el8.noarch.rpm
dnf install -y openlitespeed
systemctl start lsws
systemctl enable lsws
dnf install -y lsphp74 
dnf install -y lsphp74-*
ln -sf /usr/local/lsws/lsphp74/bin/lsphp /usr/local/lsws/fcgi-bin/lsphp5
/usr/local/lsws/bin/lswsctrl stop
/usr/local/lsws/bin/lswsctrl start
dnf -y upgrade
tee /etc/yum.repos.d/MariaDB.repo<<EOF 
[mariadb]
name = MariaDB
baseurl = http://yum.mariadb.org/10.4/centos8-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
EOF
dnf install -y boost-program-options
dnf install -y MariaDB-server MariaDB-client --disablerepo=AppStream
systemctl enable --now mariadb
mysql_secure_installation
mysql -u root -p
cd /usr/local/lsws/Example/html && wget https://wordpress.org/latest.zip && unzip latest.zip && rm latest.zip $$ cd
touch /usr/local/lsws/Example/html/wordpress/.htaccess
mkdir /usr/local/lsws/Example/html/wordpress/wp-content/upgrade
cp /usr/local/lsws/Example/html/wordpress/wp-config-sample.php /usr/local/lsws/Example/html/wordpress/wp-config.php
curl -s https://api.wordpress.org/secret-key/1.1/salt/
chown -R nobody:nobody /usr/local/lsws/Example/html/wordpress
find /usr/local/lsws/Example/html/wordpress/ -type d -exec chmod 750 {} \;
find /usr/local/lsws/Example/html/wordpress/ -type f -exec chmod 640 {} \;
vi /usr/local/lsws/Example/html/wordpress/wp-config.php

----------------------------------------  
#-mariadb> select User, Password, Host from mysql.user;
#-mariadb> CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
#-mariadb> GRANT ALL ON wordpress.* TO 'adam'@'localhost' IDENTIFIED BY 'Ax<x3$*>xB';
#-mariadb> FLUSH PRIVILEGES;
#-mariadb> SELECT user,authentication_string,plugin,host FROM mysql.user;
#-mariadb> show databases;
#-mariadb> exit
#systemctl restart mariadb
#-add
# define('FS_METHOD', 'direct');
#cat /proc/swaps
#timedatectl
#python2 --version
#python3 --version
#firewall-cmd --permanent --list-all
#dnf repolist
#netstat -pl | grep lsphp
#-setup and login to OpenLiteSpeed webadmin console(change password)
#-Setting the Administrative Password
#/usr/local/lsws/admin/misc/admpass.sh
#-visit: webadmin consol
#https:<IP Address>:7080
#-visit cockpit
#https:<IP Address>:9090
```
## root/\
```
[#vi /etc/ssh/sshd_config
#PermitRootLogin no
#systemctl reload sshd]
```
## epel-release/\
```
dnf install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
dnf update
dnf config-manager --set-enabled PowerTools
```
## remi-release/\
```
dnf install -y https://rpms.remirepo.net/enterprise/remi-release-8.rpm
#dnf repolist
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
sudo /usr/local/lsws/bin/lswsctrl start
#netstat -pl | grep lsphp
#-setup and login to OpenLiteSpeed webadmin console(change password)
#-Setting the Administrative Password
#/usr/local/lsws/admin/misc/admpass.sh
#-visit: webadmin consol
#https:<IP Address>:7080
#-visit cockpit
#https:<IP Address>:9090

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
-mariadb> select User, Password, Host from mysql.user;
-mariadb> CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
-mariadb> GRANT ALL ON wordpress.* TO 'adam'@'localhost' IDENTIFIED BY 'Ax<x3$*>xB';
-mariadb> FLUSH PRIVILEGES;
-mariadb> SELECT user,authentication_string,plugin,host FROM mysql.user;
-mariadb> show databases;
-mariadb> exit
```
## Wordpress/\
```
cd /usr/local/lsws/Example/html && wget https://wordpress.org/latest.zip && unzip latest.zip && rm latest.zip
touch /usr/local/lsws/Example/html/wordpress/.htaccess
mkdir /usr/local/lsws/Example/html/wordpress/wp-content/upgrade
cp /usr/local/lsws/Example/html/wordpress/wp-config-sample.php /usr/local/lsws/Example/html/wordpress/wp-config.php
curl -s https://api.wordpress.org/secret-key/1.1/salt/
vi /usr/local/lsws/Example/html/wordpress/wp-config.php
-add
 define('FS_METHOD', 'direct');
chown -R nobody:nobody /usr/local/lsws/Example/html/wordpress
find /usr/local/lsws/Example/html/wordpress/ -type d -exec chmod 750 {} \;
find /usr/local/lsws/Example/html/wordpress/ -type f -exec chmod 640 {} \;
```
## Configure OpenLiteSpeed with PHP 7.4/\
```
#Server Configuration>External App>+ LiteSpeed SAPI App> edit 
#Listeners>80
#-add:
-Name: lsphp74
-Address: uds://tmp/lshttpd/lsphp74.sock
-Notes: lsphp74 for OpenLiteSpeed
-Max Connections: 35
-Initial Request Timeout (secs): 60
-Retry Timeout (secs): 0
-Command: $SERVER_ROOT/lsphp74/bin/lsphp
#Listener>Default>view>Address Settings>edit>80>save
# Testing http://IP
# Virtual Hosts> View:
# General:-Document Root:$VH_ROOT/html/wordpress/
          -Index Files yes / index.php index.html
# Rewrite:Rewrie Control>yes yes
# Security:click the Delete button next to SampleProtectedArea within the Realms List table
# Context:delete the /protected/ context that was associated with the security realm you just deleted
# Graceful Restart
```
## Name-Based Virtual Hosting/\
```
cd /usr/local/lsws && mkdir -p Example2/{conf,html,logs} && chown lsadm:lsadm Example2/conf
#- Virtual Hosts 
Example2
$SERVER_ROOT/Example2/
$SERVER_ROOT/conf/vhosts/Example2/vhconf.conf
#-Listner(default80)>Virtual Host Mappings>add domaine

#Virtual Hosts>External App>+ LiteSpeed SAPI App> edit 
#Listeners>80
#-add:
-Name: lsphp74
-Address: uds://tmp/lshttpd/lsphp74.sock
-Notes: lsphp74 for OpenLiteSpeed
-Max Connections: 35
-Initial Request Timeout (secs): 60
-Retry Timeout (secs): 0
-Command: $SERVER_ROOT/lsphp74/bin/lsphp
#Listener>Default>view>Address Settings>edit>80>save
# Testing http://IP
# Virtual Hosts> View:
# General:-Document Root:$VH_ROOT/html/wordpress/
          -Index Files yes / index.php index.html
# Rewrite:Rewrie Control>yes yes
# Security:click the Delete button next to SampleProtectedArea within the Realms List table
# Context:delete the /protected/ context that was associated with the security realm you just deleted
# Graceful Restart
Listeners> map add domaine
virtualhost > Document Root: $SERVER_ROOT/Example2/html/wordpress2
              General> add domaine
reboot and test            
cd /usr/local/lsws/Example2/html && wget https://wordpress.org/latest.zip && unzip latest.zip && rm latest.zip
touch /usr/local/lsws/Example2/html/wordpress2/.htaccess
mkdir /usr/local/lsws/Example2/html/wordpress2/wp-content/upgrade
cp /usr/local/lsws/Example2/html/wordpress2/wp-config-sample.php /usr/local/lsws/Example2/html/wordpress2/wp-config.php
curl -s https://api.wordpress.org/secret-key/1.1/salt/
vi /usr/local/lsws/Example2/html/wordpress2/wp-config.php
-add
 define('FS_METHOD', 'direct');

find /usr/local/lsws/Example2/html/wordpress2/ -type d -exec chmod 750 {} \;
find /usr/local/lsws/Example2/html/wordpress2/ -type f -exec chmod 640 {} \;              
chown -R nobody:nobody /usr/local/lsws/Example2/html/wordpress2 

mysql -u root -p
-mariadb> select User, Password, Host from mysql.user;
-mariadb> CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
-mariadb> GRANT ALL ON wordpress.* TO 'adam'@'localhost' IDENTIFIED BY 'Ax<x3$*>xB';
-mariadb> FLUSH PRIVILEGES;
-mariadb> SELECT user,authentication_string,plugin,host FROM mysql.user;
-mariadb> show databases;
-mariadb> exit
systemctl restart mariadb
reboot

```
