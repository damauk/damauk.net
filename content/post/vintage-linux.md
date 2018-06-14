---
title: "Vintage Linux"
date: 2018-06-10
tags: [linux,retro]
draft: true
---

Getting new linux to run on old hardware is pretty easy. Getting old Linux to run on new hardware is an entirely different beast. I have loved Linux since I was 12 and when I dug through my old books and found my old copy of "Red Hat Linux Unleashed" from 1998 which contains a CD with Red Hat 5.2 (Not to be confused with Red Hat *Enterprise* Linux) I was pretty excited. My excitement died pretty quickly when I realised I won't be able to install the system on actual hardware since I don't have any old VGA CRT monitors laying around.

```
$ isoinfo -d -i /dev/cdrom | grep -i -E 'block size|volume size'
    Logical block size is: 2048
    Volume size is: 249506

$ dd if=/dev/cdrom of=redhat5_2.iso bs=<block size from above> count=<volume size from above>

$ qemu-img create redhat5_2.img 2G
$ ls -lh redhat5_2.img
    -rw-r--r-- 1 damauk damauk 2.0G Jun 10 09:54 redhat5_2.img

$ sudo qemu-system-i386 -hda redhat5_2.img -boot d -cdrom ./redhat5_2.iso -m 512 -vga cirrus -enable-kvm

```


# Then install the system. When it tells you to eject do the following:
press and hold <ctrl> + <alt> + <shift> + <2>
This will drop you into the qemu monitor
then type
block info
obtain the device that has the iso you used in it in my case it is cd0
eject -f ide1-cd0
Then press and hold <ctrl> + <alt> + <shift> + <1>

Now hit enter on the QEMU and you are ready to go.