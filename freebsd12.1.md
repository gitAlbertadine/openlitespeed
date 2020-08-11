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


```
