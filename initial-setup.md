## script
```
passwd
adduser said
passwd said
gpasswd -a said wheel
rsync --archive --chown=$USER:$USER ~/.ssh /home/said
chown -R said:said /home/said/.ssh
yum check-update
yum update
yum install -y firewalld firewall-config firewall-applet
systemctl start firewalld
systemctl unmask --now firewalld.service
firewall-cmd --permanent --add-service=ssh --zone=public
firewall-cmd --permanent --add-service=http
firewall-cmd --permanent --add-service=https
firewall-cmd --reload
systemctl enable --now firewalld.service
timedatectl set-timezone America/New_York
yum install -y chrony
systemctl start chronyd
systemctl enable chronyd
systemctl restart chronyd
yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
yum update
yum install -y https://rpms.remirepo.net/enterprise/remi-release-8.rpm
yum install -y htop
fallocate -l 1G /swapfile
dd if=/dev/zero of=/swapfile bs=1024 count=1048576
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile
sh -c 'echo "/swapfile none swap sw 0 0" >> /etc/fstab'
rpm -Uvh http://rpms.litespeedtech.com/centos/litespeed-repo-1.1-1.el8.noarch.rpm
yum install -y openlitespeed
systemctl start lsws
systemctl enable lsws
yum install -y lsphp74 lsphp74-common lsphp74-mysqlnd lsphp74-process lsphp74-mbstring lsphp74-mcrypt lsphp74-pdo lsphp74-gd lsphp74-opcache lsphp74-bcmath 
lsphp74-xml lsphp74-imap lsphp74-soap
```
## shared object libraries:(.so)/\
```
-ctest1.c
void ctest1(int *i)
{
   *i=5;
}
-ctest2.c
void ctest2(int *i)
{
   *i=100;
}
-prog.c
#include <stdio.h>
void ctest1(int *);
void ctest2(int *);
int main()
{
   int x;
   ctest1(&x);
   printf("Valx=%d\n",x);

   return 0;
}

-Compile the library functions: 
#gcc -Wall -fPIC -c ctest1.c ctest2.c
-Generate the shared library: 
#gcc -shared -Wl,-soname,libctest.so.1 -o libctest.so.1.0 ctest1.o ctest2.o  (-This generates the library libctest.so.1.0)
-Move to /usr/lib64/ directory:
#mv libctest.so.1.0 /usr/lib64
#ln -sf /usr/lib64/libctest.so.1.0 /usr/lib64/libctest.so.1
#ln -sf /usr/lib64/libctest.so.1 /usr/lib64/libctest.so
-Compile program for use with a shared library: 
#gcc -Wall -L/usr/lib64 prog.c -lctest -o prog
#./prog
-Investigate error/List library dependencies
#ldd libctest.so
-add program to .bash_profile
-export PATH=$PATH:/opt
-execute from anywhere (prog)
```

## Initial setup/\
```
#rpm -q centos-release
passwd
adduser said
passwd said
gpasswd -a said wheel
rsync --archive --chown=$USER:$USER ~/.ssh /home/said
chown -R said:said /home/said/.ssh

yum check-update
yum update

#firewalld/\
yum install -y firewalld firewall-config firewall-applet
systemctl start firewalld
systemctl unmask --now firewalld.service
firewall-cmd --permanent --add-service=ssh --zone=public
firewall-cmd --permanent --add-service=http
firewall-cmd --permanent --add-service=https
#sudo firewall-cmd --permanent --remove-service=ssh
#sudo firewall-cmd --permanent --add-port=8080/tcp
#sudo firewall-cmd --get-services
firewall-cmd --reload
systemctl enable --now firewalld.service
#sudo firewall-cmd --permanent --list-all
```
## root/\
```
#vi /etc/ssh/sshd_config
#PermitRootLogin no
#systemctl reload sshd
```
## chrony/\
```
timedatectl set-timezone America/New_York
#timedatectl
yum install -y chrony
systemctl start chronyd
systemctl enable chronyd
systemctl restart chronyd
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
## swap/\
```
yum install -y htop
fallocate -l 1G /swapfile
dd if=/dev/zero of=/swapfile bs=1024 count=1048576
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile
sh -c 'echo "/swapfile none swap sw 0 0" >> /etc/fstab'
htop
#cat /proc/swaps
```
## php7.4/\
```
#yum module list php
yum module enable php:remi-7.4 -y
yum install -y php php-cli php-common
```
## openlitespeed/\
```
rpm -Uvh http://rpms.litespeedtech.com/centos/litespeed-repo-1.1-1.el8.noarch.rpm
#yum repolist
yum install -y openlitespeed
systemctl start lsws
systemctl enable lsws
yum install -y lsphp74 lsphp74-common lsphp74-mysqlnd lsphp74-process lsphp74-mbstring lsphp74-mcrypt lsphp74-pdo lsphp74-gd lsphp74-opcache lsphp74-bcmath 
lsphp74-xml lsphp74-imap lsphp74-soap
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
## adm/\
```
firewall-cmd --add-port=7080/tcp --permanent
firewall-cmd --reload
cd /usr/local/lsws/admin/misc
./admpass.sh
http://server_domain_or_IP:7080
said->Ax..xB
ln -sf /usr/local/lsws/lsphp74/bin/lsphp /usr/local/lsws/fcgi-bin/lsphp
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
## name-based virtual hosting/\
```
cd /usr/local/lsws && mkdir Example2 && mkdir Example2/{conf,html,logs} && chown lsadm:lsadm Example2/conf && cd
-............
```
## Wordpress/\
```
-mysql -u root -p
-MariaDB [(none)]> grant all privileges on wordpress.* to wordpress@localhost identified by 'wordpress';
-exit
yum install -y wget unzip && cd /usr/local/lsws/Example2/html && wget https://wordpress.org/latest.zip && unzip latest.zip && rm latest.zip
chown -R nobody:nobody wordpress
```

## mariadb-connector-c-3.0.7-1.el8.x86_64.rpm/\
```
yum install http://mirror.centos.org/centos/8/AppStream/x86_64/os/Packages/mariadb-connector-c-3.0.7-1.el8.x86_64.rpm
```






```
