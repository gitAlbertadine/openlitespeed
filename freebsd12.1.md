#alias l   ls -lA
```
ssh freebsd@164.90.239.22
echo $SHELL
  /bin/sh
sudo chsh -s /bin/tcsh freebsd
ctrl+d
echo $SHELL
 /bin/tcsh
sudo chsh -s /bin/sh freebsd
ctrl+d
echo $SHELL
 /bin/sh
sudo pkg install bash
bash
sudo chsh -s /usr/local/bin/bash freebsd
sudo chsh -s /usr/local/bin/bash root
ctrl+d
vim ~/.bash_profile
source ~/.bash_profile 
add 
    export PAGER=less
    export EDITOR=ee
CTRL+C
exit
enter
-password for root:
sudo passwd
sudo portsnap fetch
sudo portsnap extract

sudo portsnap fetch
sudo portsnap update
or
sudo portsnap fetch update

cd /usr/ports/devel/pcre; make install clean; rehash;
cd /usr/ports/devel/rcs; make install clean; rehash;
cd /usr/ports/dns/udns; make install clean; rehash;
cd /usr/ports/textproc/expat2; make install clean; rehash;
cd /usr/ports/security/openssl; make install clean; rehash;
cd /usr/ports/lang/perl5.26; make install clean; rehash;

./configure --with-pcre=/usr/local --with-openssl=/usr --enable-http2


...................to be continued

```
