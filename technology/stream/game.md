# Game

## [Raspberry remote gaming solution](https://www.youtube.com/watch?v=sjO95WmyCc0)

## Linux remote gaming solutions 

### Config

* Moonlight \(NVidia\)
* NoMachine
* X2Go
* Xorg Forwarding

## Windows remote gaming solution

#### **GPU MEMORY SPLIT**

* Parsec

### [Parsec](https://www.youtube.com/watch?v=sjO95WmyCc0) \( For raspberry \) 

Enter **204**, accept the option, and exit choosing to reboot.

Once the installation and set up of Raspbian is complete, verify that the GPU memory split is 128mb or higher. Please run this command `sudo raspi-config`. Navigate down to `7 Advanced Options` then `A3 Memory Split` Enter 204, accept the option, and exit choosing to reboot.

**INSTALL AND RUN PARSEC**

After the Pi has rebooted, download Parsec from here 

```text
wget https://s3.amazonaws.com/parsec-build/package/parsec-rpi.deb
sudo dpkg -i parsec-rpi.deb

# Run the Parsec Client with parsecd from any directory.
parsecd
```

If you're having trouble logging to Parsec, please note that the default keyboard is UK QWERTY, so you may need to change this to US QWERTY to make sure your keyboard works correctly.

If you prefer to run the Parsec Application headless, type `parsecd peer_id=YOUR_PEER_ID` from any directory. You can find your Peer ID from the Parsec application on your computer and right clicking the computer with the crown.

#### **RASPBERRY PI WIFI**

The native Wifi adapter on the Pi is not good. We recommend using ethernet or buying one of [these](https://www.amazon.com/Edimax-Adapter-Supports-MU-MIMO-EW-7822ULC/dp/B01MY7PL10/ref=sr_1_2?s=electronics&ie=UTF8&qid=1516079377&sr=1-2&keywords=edimax+wifi+adapter+5+ghz). Make sure the one you choose supports 5 Ghz Wifi.

#### **SETTING UP XBOX CONTROLLERS ON PI**

For the Raspberry Pi, you can install Xbox controller support. 

```text
sudo apt install xboxdrv
```

Unfortunately, however, if you have an Xbox One S and want to use the Bluetooth connection, you'll need [this driver](https://github.com/atar-axis/xpadneo/). 

#### **SETTING UP OTHER BLUETOOTH CONTROLLERS**

[This article](https://lifehacker.com/everything-you-need-to-set-up-bluetooth-on-the-raspberr-1768482065) gives a great explanation of setting up Bluetooth controllers on the Pi.

#### **RPI CONFIGURATION SETTINGS**

After installing Parsec for the first time on your Pi or reinstalling it, run the app one time by typing `parsec`. Once you run Parsec once, the configuration file is located in `home/pi/.parsec`. If you don't see the config file there, it might be hidden. Run this command - `ls -al`.

**References**

* [https://www.youtube.com/watch?v=sjO95WmyCc0&t=288s](https://www.youtube.com/watch?v=sjO95WmyCc0&t=288s)
* [https://www.youtube.com/watch?v=FwoFi1wpBOY](https://www.youtube.com/watch?v=FwoFi1wpBOY)
* [https://www.youtube.com/watch?v=FHKpWyovvws](https://www.youtube.com/watch?v=FHKpWyovvws)

-

