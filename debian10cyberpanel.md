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
