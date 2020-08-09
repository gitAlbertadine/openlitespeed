## openlitespeed(not ok)
```
apt update && apt upgrade
passwd
adduser said
usermod -aG sudo said
apt install -y software-properties-common build-essential
apt install -y ufw htop rsync
ufw default deny incoming
ufw default allow outgoing
ufw allow OpenSSH
ufw allow 443/tcp
ufw allow 80/tcp
ufw allow 8090/tcp
ufw allow 9090/tcp
ufw enable
rsync --archive --chown=$USER:$USER ~/.ssh /home/said
chown -R said:said /home/said/.ssh
apt install -y perl libperl-dev libgd3 libgd-dev libgeoip1 libgeoip-dev geoip-bin libxml2 libxml2-dev libxslt1.1 libxslt1-dev
apt autoremove
apt install chrony
timedatectl set-timezone America/New_York
systemctl restart chronyd
sudo fallocate -l 1G /swapfile
sudo dd if=/dev/zero of=/swapfile bs=1024 count=1048576
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
echo "/swapfile swap swap defaults 0 0" | sudo tee -a /etc/fstab
sudo mount -a

apt install build-essential libexpat1-dev libgeoip-dev libpcre3-dev libudns-dev zlib1g-dev libssl-dev libxml2 libxml2-dev rcs libpng-dev libpng-dev openssl autoconf g++ make openssl libssl-dev libcurl4-openssl-dev libcurl4-openssl-dev pkg-config libsasl2-dev libzip-dev

wget https://openlitespeed.org/packages/openlitespeed-1.5.2.tgz
tar -xvzf openlitespeed-1.5.2.tgz
cd openlitespeed
sh install.sh
systemctl start lsws
systemctl enable lsws
```
