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

sudo yum groupinstall 'Development Tools'
sudo yum install libxml2-devel.x86_64 openssl-devel.x86_64 bzip2-devel.x86_64 libcurl-devel.x86_64 libpng-devel.x86_64 libXpm-devel.x86_64 freetype-devel.x86_64 gmp-devel.x86_64  openldap-devel.x86_64    zlib-devel.x86_64 mysql-devel.x86_64 ncurses-devel.x86_64 pcre-devel.x86_64 unixODBC-devel.x86_64  sqlite-devel.x86_64  readline-devel.x86_64  net-snmp-devel.x86_64  libxslt-devel.x86_64 
#-local(root)
scp /home/said/Desktop/LiteSpeed/lsws-5.4.8-ent-x86_64-linux.tar.gz root@161.35.124.152:~
chmod 755 lsws-5.4.8-ent-x86_64-linux.tar.gz
tar -zxvf lsws-5.4.8-ent-x86_64-linux.tar.gz
cd lsws-5.4.8
./install



```
