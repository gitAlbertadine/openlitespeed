## ubuntu20
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

wget -O - http://rpms.litespeedtech.com/debian/enable_lst_debian_repo.sh | sudo bash
dnf install -y lsphp74 
dnf install -y lsphp74-*
ln -sf /usr/local/lsws/lsphp74/bin/lsphp /usr/local/lsws/fcgi-bin/lsphp5
sudo /usr/local/lsws/bin/lswsctrl start
#netstat -pl | grep lsphp

/lib/systemd/systemd-sysv-install enable lsws
systemctl start lsws

curl -sS https://downloads.mariadb.com/MariaDB/mariadb_repo_setup | sudo bash
cat /etc/apt/sources.list.d/mariadb.list
apt update
apt install mariadb-server mariadb-client libmariadb3 mariadb-backup mariadb-common
#*to remove purge and sudo rm -rf /var/lib/mysql/
mysql_secure_installation
systemctl restart mariadb.service
mysql -u root -p

apt install net-tools
netstat -pl | grep lsphp

```
