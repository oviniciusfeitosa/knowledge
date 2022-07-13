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

### More memory specs

```
$ sudo apt install i2c-tools 
$ decode-dimms

# decode-dimms version 4.3

Memory Serial Presence Detect Decoder
By Philip Edelbrock, Christian Zuckschwerdt, Burkart Lingner,
Jean Delvare, Trent Piepho and others


Decoding EEPROM: /sys/bus/i2c/drivers/ee1004/0-0050
Guessing DIMM is in                              bank 1
Kernel driver used                               ee1004

---=== SPD EEPROM Information ===---
EEPROM CRC of bytes 0-125                        OK (0x12E4)
# of bytes written to SDRAM EEPROM               384
Total number of bytes in EEPROM                  512
Fundamental Memory type                          DDR4 SDRAM
SPD Revision                                     1.1
Module Type                                      SO-DIMM
EEPROM CRC of bytes 128-253                      OK (0x55EF)

---=== Memory Characteristics ===---
Maximum module speed                             3200 MT/s (PC4-25600)
Size                                             8192 MB
Banks x Rows x Columns x Bits                    16 x 16 x 10 x 64
SDRAM Device Width                               8 bits
Ranks                                            1
Primary Bus Width                                64 bits
AA-RCD-RP-RAS (cycles)                           22-22-22-52
Supported CAS Latencies                          24T, 22T, 21T, 20T, 19T, 18T, 17T, 16T, 15T, 14T, 13T, 12T, 11T, 10T

---=== Timings at Standard Speeds ===---
AA-RCD-RP-RAS (cycles) as DDR4-3200              22-22-22-52
AA-RCD-RP-RAS (cycles) as DDR4-2933              21-21-21-47
AA-RCD-RP-RAS (cycles) as DDR4-2666              19-19-19-43
AA-RCD-RP-RAS (cycles) as DDR4-2400              17-17-17-39
AA-RCD-RP-RAS (cycles) as DDR4-2133              15-15-15-35
AA-RCD-RP-RAS (cycles) as DDR4-1866              13-13-13-30
AA-RCD-RP-RAS (cycles) as DDR4-1600              11-11-11-26

---=== Timing Parameters ===---
Minimum Cycle Time (tCKmin)                      0.625 ns
Maximum Cycle Time (tCKmax)                      1.600 ns
Minimum CAS Latency Time (tAA)                   13.750 ns
Minimum RAS to CAS Delay (tRCD)                  13.750 ns
Minimum Row Precharge Delay (tRP)                13.750 ns
Minimum Active to Precharge Delay (tRAS)         32.000 ns
Minimum Active to Auto-Refresh Delay (tRC)       45.750 ns
Minimum Recovery Delay (tRFC1)                   350.000 ns
Minimum Recovery Delay (tRFC2)                   260.000 ns
Minimum Recovery Delay (tRFC4)                   160.000 ns
Minimum Four Activate Window Delay (tFAW)        21.000 ns
Minimum Row Active to Row Active Delay (tRRD_S)  2.500 ns
Minimum Row Active to Row Active Delay (tRRD_L)  4.900 ns
Minimum CAS to CAS Delay (tCCD_L)                5.000 ns
Minimum Write Recovery Time (tWR)                15.000 ns
Minimum Write to Read Time (tWTR_S)              2.500 ns
Minimum Write to Read Time (tWTR_L)              7.500 ns

---=== Other Information ===---
Package Type                                     Monolithic
Maximum Activate Count (MAC)                     Unlimited
Post Package Repair                              One row per bank group
Soft PPR                                         Supported
Module Nominal Voltage                           1.2 V
Thermal Sensor                                   No

---=== Physical Characteristics ===---
Module Height                                    30 mm
Module Thickness                                 2 mm front, 2 mm back
Module Reference Card                            A revision 1

---=== Manufacturer Data ===---
Module Manufacturer                              Smart Modular
DRAM Manufacturer                                Smart Modular
Manufacturing Location Code                      0x06
Manufacturing Date                               2020-W40
Assembly Serial Number                           0x05F7694E
Part Number                                      SMS4WEC8C1K0446FCG  


Number of SDRAM DIMMs detected and decoded: 1

```
