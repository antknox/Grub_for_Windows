#grub for windows

##必要源文件

		grldr
		grldr.mbr
		grldr.exe

		ini

###XP

      grldr

      boot.ini>>
```ini
[boot loader]
[operating systems]
C:\grldr="Grub For DOS"
```

###Windows 7

      grldr.mbr

      boot.ini>
```ini
[boot loader]
[operating systems]
C:\grldr..mbr="Grub For DOS"
```
      menu.lst
```lst
timeout=5

default 0

#Boot

#0

title 01 Boot Windows 7

rootnoverify (hd0,0)

chainloader (hd0,0)

boot

#1

title 02 Boot Ubuntu xx.xx_x86

root (hd0,2)

kernel (hd0,2)/boot/grub/i386-pc/core.img

boot

#2

title 03 Boot Upan Move

rootnoverify (hd1,0)

chainloader +1

boot

#寻找

#3

title 04 Boot Ubuntu (all)

find --set-root /boot/grub/i386-pc/core.img

kernel /boot/grub/i386-pc/core.img

boot

#Install

#4

title 05 Install Ubuntu 12.04_x86

root (hd0,0)

kernel (hd0,0)/12.04/vmlinuz boot=casper iso-scan/filename=/12.04/ubuntu-12.04-desktop-i386.iso ro quiet splash  locale=zh_CN.UTF-8

initrd (hd0,0)/12.04/initrd.lz

#5

title 06 Install Ubuntu 13.10_x64

root (hd0,0)

kernel (hd0,0)/13.10/vmlinuz.efi boot=casper iso-scan/filename=/13.10/ubuntu-13.10-desktop-amd64.iso ro quiet splash  locale=zh_CN.UTF-8

initrd (hd0,0)/13.10/initrd_64.lz

#6

title 07 Install Ubuntu 13.10_x86

root (hd0,0)

kernel (hd0,0)/13.10/vmlinuz boot=casper iso-scan/filename=/13.10/ubuntu-13.10-desktop-i386.iso ro quiet splash  locale=zh_CN.UTF-8

initrd (hd0,0)/13.10/initrd.lz

#7

title 08 Boot From First CDROM

cdrom --init

map --hook

chainloader (cd0)

boot

#8

title 09 Reboot System

reboot
```