# Specs

## Workstation

### Desktop

``````
$ screenfetch                 
                          ./+o+-       vinnyfs89@Desktop
                  yyyyy- -yyyyyy+      OS: Ubuntu 20.04 focal
               ://+//////-yyyyyyo      Kernel: x86_64 Linux 5.4.0-52-generic
           .++ .:/++++++/-.+sss/`      Uptime: 8m
         .:++o:  /++++++++/:--:/-      Packages: 1678
        o:+o+:++.`..```.-/oo+++++/     Shell: zsh 5.8
       .:+o:+o/.          `+sssoo+/    Resolution: 1920x1080
  .++/+:+oo+o:`             /sssooo.   DE: GNOME 3.36.4
 /+++//+:`oo+o               /::--:.   WM: Mutter
 \+/+o+++`o++o               ++////.   WM Theme: Adwaita
  .++.o+++oo+:`             /dddhhh.   GTK Theme: Dracula-pink-accent [GTK2/3]
       .+.o+oo:.          `oddhhhh+    Icon Theme: Yaru
        \+.++o+o``-````.:ohdhhhhh+     Font: Ubuntu 11
         `:o+++ `ohhhhhhhhyo++os:      Disk: 81G / 444G (20%)
           .o:`.syhhhhhhh/.oo++o`      CPU: AMD FX-8350 Eight-Core @ 8x 4GHz
               /osyyyyyyo++ooo+++/     GPU: AMD/ATI Bonaire XTX [Radeon R7 260X/360]
                   ````` +oo+++o\:     RAM: 2975MiB / 7907MiB

``````

## Show memory information

```
$ sudo dmidecode -t 16      

# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x0024, DMI type 16, 23 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 32 GB
	Error Information Handle: No Error
	Number Of Devices: 2

```
