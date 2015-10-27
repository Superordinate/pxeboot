# pxeboot
pxeboot

# pixecore
installers


This is install pixicore-PXE booting.
- Install go from moovweb/gvm:
```
bash < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer)

source /root/.gvm/scripts/gvm

apt-get install bison

gvm install go1.4

gvm use go1.4

export GOROOT_BOOTSTRAP=$GOROOT

gvm install go1.5

```
-Install pixicore:
```
git clone https://github.com/danderson/pixiecore

cd pixiecore

go build .

wget http://alpha.release.core-os.net/amd64-usr/current/coreos_production_pxe.vmlinuz

wget http://alpha.release.core-os.net/amd64-usr/current/coreos_production_pxe_image.cpio.gz

mv pixiecore /usr/bin

pixiecore -kernel coreos_production_pxe.vmlinuz -initrd coreos_production_pxe_image.cpio.gz --cmdline coreos.autologin
```
And now try to boot from another pc boot to Network to see pixicore run.
```
mkdir /tftpboot
```
-Download erpxe-1.2.tar.gz from http://sourceforge.net/projects/erpxe/files/ 
```
tar -zvxf erpxe-1.2.tar.gz

nano /etc/default/tftpd-hpa

apt-get install tftpd-hpa

apt-get update

update-rc.d tftpd-hpa defaults

apt-get install apache2

update-rc.d apache2 defaults

cp /tftpboot/bin/setup/erpxe-httpd.conf /etc/apache2/conf.d/

mkdir /etc/apache2/conf.d

cp /tftpboot/bin/setup/erpxe-httpd.conf /etc/apache2/conf.d/

apt-get install nfs-kernel-server rpcbind

cat /tftpboot/bin/setup/erpxe-exports > /etc/exports

update-rc.d rpcbind enable

apt-get install samba samba-common-bin

useradd --no-create-home -s /dev/null erpxe

cat /tftpboot/bin/setup/erpxe-smb.conf > /etc/samba/smb.conf

smbpasswd -a erpxe

smbpasswd -a root

pixiecore -kernel coreos_production_pxe.vmlinuz -initrd coreos_production_pxe_image.cpio.gz --cmdline coreos.autologin
```

# ubuntu_pxe
ubuntu pxe

This is fully Automated Ubuntu () Installation  with PXE from a board ex: BananaPi, RaspberryPi, OrangePi PC ..

-After  install pixicore-PXE booting from https://github.com/Superordinate/pixecore.git, need to https://github.com/Superordinate/ubuntu_pxe.git:
```
git clone https://github.com/Superordinate/ubuntu_pxe.git

cd /ubuntu_pxe/amd64/

sh ubuntu.sh
```
-Now try to boot from another pc boot to Network to install ubuntu 

Note: 
```
It will auto delete all partitions old.
```
User & pass for this ubuntu:
```
use: root
pass: pacopower
```

# debian_pxe
debian_jessi_pxe

This is fully Automated Debian (jessi) Installation  with PXE from a board ex: BananaPi, RaspberryPi, OrangePi PC ..

-After  install pixicore-PXE booting from https://github.com/Superordinate/pixecore.git, need to https://github.com/Superordinate/debian_pxe.git:
```
git clone https://github.com/Superordinate/debian_pxe.git

cd /debian_pxe/amd64/

sh debian.sh
```
-Now try to boot from another pc boot to Network to install debian 

Note: 
```
It will auto delete all partitions old.
```
User & pass for this debian:
```
use: root
pass: r00tme
```
