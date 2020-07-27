## Initial setup
```
#user/\
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

#root/\
#vi /etc/ssh/sshd_config
#PermitRootLogin no
#systemctl reload sshd

#chrony/\
timedatectl set-timezone America/New_York
#timedatectl
yum install -y chrony
systemctl start chronyd
systemctl enable chronyd
systemctl restart chronyd

#epel-release/\
yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
yum update
#yum repolist

#swap/\
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
