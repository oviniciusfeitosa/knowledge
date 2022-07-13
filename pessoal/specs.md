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

### Slots

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

### Capacity

```
$ sudo dmidecode -t 17

# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x0025, DMI type 17, 84 bytes
Memory Device
	Array Handle: 0x0024
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 8 GB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelA-DIMM0
	Bank Locator: BANK 0
	Type: DDR4
	Type Detail: Synchronous
	Speed: 2933 MT/s
	Manufacturer: Smart Brazil
	Serial Number: 111
	Asset Tag: 22222
	Part Number: 33333  
	Rank: 1
	Configured Memory Speed: 2933 MT/s
	Minimum Voltage: 1.25 V
	Maximum Voltage: 1.35 V
	Configured Voltage: 1.2 V
	Memory Technology: DRAM
	Memory Operating Mode Capability: Volatile memory
	Firmware Version: Not Specified
	Module Manufacturer ID: Bank 2, Hex 0x94
	Module Product ID: Unknown
	Memory Subsystem Controller Manufacturer ID: Unknown
	Memory Subsystem Controller Product ID: Unknown
	Non-Volatile Size: None
	Volatile Size: 8 GB
	Cache Size: None
	Logical Size: None

Handle 0x0026, DMI type 17, 84 bytes
Memory Device
	Array Handle: 0x0024
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 8 GB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelB-DIMM0
	Bank Locator: BANK 2
	Type: DDR4
	Type Detail: Synchronous
	Speed: 2933 MT/s
	Manufacturer: Crucial
	Serial Number: 111
	Asset Tag: 222
	Part Number: 333  
	Rank: 1
	Configured Memory Speed: 2933 MT/s
	Minimum Voltage: 1.25 V
	Maximum Voltage: 1.35 V
	Configured Voltage: 1.2 V
	Memory Technology: DRAM
	Memory Operating Mode Capability: Volatile memory
	Firmware Version: Not Specified
	Module Manufacturer ID: Bank 6, Hex 0x9B
	Module Product ID: Unknown
	Memory Subsystem Controller Manufacturer ID: Unknown
	Memory Subsystem Controller Product ID: Unknown
	Non-Volatile Size: None
	Volatile Size: 8 GB
	Cache Size: None
	Logical Size: None


```
