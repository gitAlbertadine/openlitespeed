## cyberpanel on debian
```
passwd
adduser said
usermod -aG sudo said
apt update && apt upgrade
apt install -y wget  zip unzip tar htop rsync chrony
rsync --archive --chown=$USER:$USER ~/.ssh /home/said
chown -R said:said /home/said/.ssh
fallocate -l 1G /swapfile
dd if=/dev/zero of=/swapfile bs=1024 count=1048576
chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sh -c 'echo "/swapfile none swap sw 0 0" >> /etc/fstab'
mount -a
timedatectl set-timezone America/New_York
systemctl restart chronyd
timedatectl
systemctl reboot
sudo apt install cockpit

apt install ufw
ufw default deny incoming
ufw default allow outgoing
ufw allow OpenSSH
ufw allow 8090/tcp
ufw allow 7080/tcp
ufw allow 9090/tcp
ufw allow 80/tcp
ufw allow 443/tcp
ufw allow 443/udp
ufw allow 21/tcp
ufw allow 40110-40210/tcp
ufw allow 25/tcp
ufw allow 587/tcp
ufw allow 465/tcp
ufw allow 110/tcp 
ufw allow 143/tcp
ufw allow 993/tcp
ufw allow 53/tcp
ufw allow 53/udp
ufw enable
ufw status verbose



```
