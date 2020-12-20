# Game

## [Remote gaming solution](https://www.youtube.com/watch?v=sjO95WmyCc0)

### **RASPBIAN INSTALLATION**

The installation of Parsec is very simple. Start with a fresh distribution of Raspbian. 

The Raspberry Pi Organization provides detailed installation instructions [here](https://www.raspberrypi.org/documentation/installation/installing-images/).

#### **GPU MEMORY SPLIT**

Once the installation and set up of Raspbian is complete, verify that the GPU memory split is 128mb or higher. Please run this command `sudo raspi-config`. Navigate down to:

`7 Advanced Options`

then:

`A3 Memory Split`

Enter 128, accept the option, and exit choosing to reboot.

### **INSTALL AND RUN PARSEC**

After the Pi has rebooted, download Parsec from here `wget` [`https://s3.amazonaws.com/parsec-build/package/parsec-rpi.deb`](https://s3.amazonaws.com/parsec-build/package/parsec-rpi.deb)

Please move into the directory in which you downloaded Parsec and extract the file with  `sudo dpkg -i` [`parsec-rpi.deb`](https://parsec-rpi.deb/). You may need to change the file name before doing this by changing.

Run the Parsec Client with `parsecd` from any directory.

If you're having trouble logging to Parsec, please note that the default keyboard is UK QWERTY, so you may need to change this to US QWERTY to make sure your keyboard works correctly.

If you prefer to run the Parsec Application headless, type `parsecd peer_id=YOUR_PEER_ID` from any directory. You can find your Peer ID from the Parsec application on your computer and right clicking the computer with the crown.

#### **RASPBERRY PI WIFI**

The native Wifi adapter on the Pi is not good. We recommend using ethernet or buying one of [these](https://www.amazon.com/Edimax-Adapter-Supports-MU-MIMO-EW-7822ULC/dp/B01MY7PL10/ref=sr_1_2?s=electronics&ie=UTF8&qid=1516079377&sr=1-2&keywords=edimax+wifi+adapter+5+ghz). Make sure the one you choose supports 5 Ghz Wifi.

#### **SETTING UP XBOX CONTROLLERS ON PI**

For the Raspberry Pi, you can `sudo apt-get install xboxdrv` for Xbox controller support. 

If you're using the Raspberry Pi version of Parsec, you'll need to install drivers for the controllers. The best Xbox driver we've found is xboxdrv. For the Raspberry Pi, you can `sudo apt-get install xboxdrv`.

Unfortunately, however, if you have an Xbox One S and want to use the bluetooth connection, you'll need [this driver](https://github.com/atar-axis/xpadneo/). 

#### **SETTING UP OTHER BLUETOOTH CONTROLLERS**

[This article](https://lifehacker.com/everything-you-need-to-set-up-bluetooth-on-the-raspberr-1768482065) gives a great explanation of setting up bluetooth controllers on the Pi.

#### **MOUSE POLLING RATE ON PI**

The speed at which the computer checks on its peripherals is referred to as “polling speed”. This happens very fast and usually without interaction. In the case of the Raspberry Pi, the polling speed for mice has been set by default to 62.5hz, or 62.5 times-per-second. This helps out the Pi by making it easier on the CPU, but it leads to poor performance in games and often very slow-feeling tracking speeds. What most users prefer is 125hz, that is a polling speed of 1000ms/125hz or 8ms. To set this on the Pi, perform the following commands:

`sudo nano /boot/cmdline.txt`

You should see something like:

`dwc_otg.lpm_enable=0 console=serial0,115200 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 etc…`

You need to add the parameter `usbhid.mousepoll=8` so you end up with something like this:

`dwc_otg.lpm_enable=0 console=serial0,115200 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 usbhid.mousepoll=8 etc…`

Then hit `ctrl + x` to exit, and say “Y” to save. After a reboot the mouse should feel much more responsive. The number 8 can be lowered to 1ms or even 0 to respect the USB devices internal poll rate, but be warned doing so can take a very steep toll on the Pi’s modest CPU and is not recommended.

#### **RPI CONFIGURATION SETTINGS**

After installing Parsec for the first time on your Pi or reinstalling it, run the app one time by typing `parsec`. Once you run Parsec once, the configuration file is located in `home/pi/.parsec`. If you don't see the config file there, it might be hidden. Run this command - `ls -al`.

-

