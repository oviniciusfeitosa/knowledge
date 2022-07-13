# How to

## Topics

* ****[**Proxy**](proxy.md)****
* ****[**SSH**](ssh.md)****
* ****[**ZSH**](zsh.md)****

## Download files from the cloud

{% hint style="info" %}
* Send content to WeTransfer cloud-like&#x20;
* Download using **wget**
{% endhint %}

### Installing wget

```
sudo apt install wget
```

### Download a single file

```
wget https://wordpress.org/latest.zip
```

### Save the downloaded file under a different name <a href="#using-wget-command-to-save-the-downloaded-file-under-different-name" id="using-wget-command-to-save-the-downloaded-file-under-different-name"></a>

To save the downloaded file under a different name, pass the `-O` option followed by the chosen name.

```
wget -O latest-wordpress.zip https://wordpress.org/latest.zip
```

### How to download in the background mode with wget  <a href="#how-to-download-in-background-with-wget" id="how-to-download-in-background-with-wget"></a>

To download in the background, use the option `-b` . In the following example, we are downloading the OpenSuse iso file in the background.

```
wget -b https://download.opensuse.org/tumbleweed/iso/openSUSE-Tumbleweed-DVD-x86_64-Current.iso
```

### Download all files from FTP

```
wget -r 'ftp://username:password@ip/directoryname'
```

## Download / Upload Files

### Single file from remote to local

```
scp remoteuser@remoteserver:/remote/folder/myfile.txt  myfile.txt
```

### Multiple files from local to remote

```
scp myfile.txt myfile2.txt remoteuser@remoteserver:/remote/folder/
```

### All files from local to remote

```
scp * remoteuser@remoteserver:/remote/folder/
```

### All files and folders recursively from local to remote

```
scp -r * remoteuser@remoteserver:/remote/folder/
```

#### References: [Simplified Guide](https://www.simplified.guide/ssh/copy-file)

## DNS

### Custom DNS&#x20;

```
$ vim  /etc/resolv.conf   

nameserver 8.8.8.8
nameserver 8.8.4.4
```

### Custom DNS servers for /etc/resolv.conf

To define a custom DNS:

* First, install **`resolvconf`** and follow the commands bellow

```bash
sudo apt install resolvconf -y
```

* Put the nameservers from Google inside the file**`/etc/resolvconf/resolv.conf.d/head`**

```bash
sudo sh -c "echo \"nameserver 8.8.8.8
nameserver 8.8.4.4\" >> /etc/resolvconf/resolv.conf.d/head"

sudo sh -c "echo \"nameserver 8.8.8.8
nameserver 8.8.4.4\" >> /etc/resolvconf/resolv.conf.d/base"
```

*   Update Resolvconf

    ```
    sudo resolvconf -u
    ```

    \

* Restart the resolvconf service

```bash
sudo service resolvconf restart
```

## Get current IP from the shell

```bash
remoteHost=$(dig +short myip.opendns.com @resolver1.opendns.com)
echo $remoteHost
```

## Stream audio

```bash
sudo apt install -y pulseaudio pavucontrol
```

* `Alt + F2`  and type `pavucontrol`
* Select `Recording` tab
* Change to `Internal audio monitor`

## Search inside files recursively&#x20;

```
grep -rli "my-name"
```

## Display Usage in Megabytes and Gigabytes

```
df -h
```

### Display a Specific File System

```
df –h /dev/sda2
```

## Show size of folders

```
sudo du -shc /var/*
```

## Empty trash

```
rm -rf ~/.local/share/Trash/*
```

## Search and replace inside the file

```
sed -i 's/SEARCH_REGEX/REPLACEMENT/g' INPUTFILE
```

## Network

### Check network ports in use

```
sudo netstat -tlnp | grep 80
```

### Check opened network ports of the server

```
nmap HOST

## Example

nmap google.com
nmap 55.1.22.5.68
```

### Open network ports

```
# Openning 8080 port
 
 sudo iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
```

### Open Firewall ports

To open ports on the firewall, using the **iptables** command is possible specifying the desired port. Using the example below, just replace port **8888** with the desired port.

```
$ iptables -I INPUT -p tcp --dport 8888 -j ACCEPT
$ iptables -t filter -I FORWARD -i eth2 -o etho -m multiport --dport 8888 -j ACCEPT
```

## Logs

### Show real-time logs from OS

```
tail -f /var/log/syslog

# Or you can use journalctl
# journalctl -f
```

## Environment

### Set Global environment

```
sudo sh -c "echo MY_GLOBAL_ENV_TO_MY_CURRENT_DIR=$(pwd)" >> /etc/environment"
```

### Set local environment

```
env MY_GLOBAL_ENV_TO_MY_CURRENT_DIR=$(pwd)
```

### Unset local environment

```
unset MY_GLOBAL_ENV_TO_MY_CURRENT_DIR
```

## Startup

### Show all service status

```
sudo service --status-all 
```

### Exec commands at startup

```

sudo vim /etc/init.d/rc.local

    #!/bin/bash

    #command1
    #command2
    exit 0;

sudo chmod ugo+x /etc/init.d/rc.local

update-rc.d rc.local defaults
```

## PPA

### Remove installed PPA repository

Use the "--remove" flag, similar to how the PPA was added:

```
sudo add-apt-repository --remove ppa:whatever/ppa
```

As a safer alternative, you can install "ppa-purge":

```
sudo apt-get install ppa-purge
```

And then remove the PPA, downgrading gracefully packages it provided to packages provided by official repositories:

```
sudo ppa-purge ppa:whatever/ppa
```

Note that this will uninstall packages provided by the PPA, but not those provided by the official repositories. If you want to remove them, you should tell it to apt:

```
sudo apt-get purge package_name
```

You can also remove PPAs by deleting the .list files from `/etc/apt/sources.list.d` directory.

Last but not least, you can also disable or remove PPAs from the "Software Sources" section in Ubuntu Settings with a few clicks of your mouse (no terminal needed).

### **Execute "add-apt-repository" without press enter**

{% hint style="info" %}
**--force-yes**

Force yes; this is a dangerous option that will cause apt to continue without prompting if it is doing something potentially harmful. It **should not** be used except in very special situations. Using force-yes can potentially destroy your system! Configuration Item: APT::Get::force-yes.
{% endhint %}

```
# Example
sudo add-apt-repository ppa:ondrej/php --force-yes
```

## Create an alias for shell commands

* Add the script below at end of the file  **`~/.profile`**&#x20;

```
alias hello_world="echo \"Hello World!\""
```

* Then type your alias directly

```
hello_world
# output: Hello World
```

## Update packages less noisy

```
apt-get -qq update
```

## Revalidade ca-certificates

```
sudo apt-get install -y --reinstall ca-certificates
```

##

## Add multi-touch to your Linux distribution

To do it, make sure to do the steps below:

```
sudo gpasswd -a $USER input
sudo apt install xdotool wmctrl libinput-tools
git clone https://github.com/bulletmark/libinput-gestures
cd libinput-gestures
sudo ./libinput-gestures-setup install
touch ~/.config/libinput-gestures.conf
```

* Paste the content below inside **`~/.config/libinput-gestures.conf`**:

```
gesture swipe up 3 xdotool key super+Down  
gesture swipe left 3 xdotool key super+Right  
gesture swipe right 3 xdotool key super+Left  
```

* `After that execute the commands below`

```
libinput-gestures-setup autostart
libinput-gestures-setup start
libinput-gestures-setup restart
```

### References:

* [https://github.com/bulletmark/libinput-gestures](https://github.com/bulletmark/libinput-gestures)
* [https://www.youtube.com/watch?v=ci6YbQGx3c4](https://www.youtube.com/watch?v=ci6YbQGx3c4)

## Get SO information

```
sudo apt-get install screenfetch -y
screenfetch
```

## Know where the program was installed

```
which php
```

## Show any configured swap

```
sudo swapon --show
```

## Observe and monitor system memory usage

{% hint style="info" %}
* "-h" means Human Mode
  * Shows values in Mega or Giga
{% endhint %}

```
free -h
```

## Downgrade Ubuntu Linux system version

{% hint style="info" %}
This example will be used a downgrade from Ubuntu 20.10 to 20.04.

* **From**
  * **Version**: Ubuntu 20.10
  * **Name**: Gorilla Grovy
  * **Codename**: grovy
* **To**
  * **Version**: Ubuntu 20.04
  * **Name**: Focal Fossa
  * **Codename**: focal
{% endhint %}

### **Downgrade sources.list**

```
sudo sed -i 's/groovy/focal/g' /etc/apt/sources.list
```

### **Pin packages**

{% hint style="info" %}
Open ** `/etc/apt/preferences`** file and enter the following content while replacing the codename of the system codename you aim to downgrade to.
{% endhint %}

{% code title="/etc/apt/preferences" %}
```
Package: *
Pin: release a=focal v=20.04
Pin-Priority: 1001
```
{% endcode %}

### **Downgrade Ubuntu system**

```
sudo apt update ; sudo apt upgrade ; sudo apt dist-upgrade
```

{% hint style="warning" %}
If you found any errors try this:

```
sudo apt --fix-broken install
sudo dpkg --configure -a
sudo apt dist-upgrade
sudo apt install ubuntu-desktop
```
{% endhint %}

## Find and remove folder recursively

```
# Example: node_modules
  sudo find . -type d -name node_modules -exec rm -r {} \;
```

## Open Mac External Harddrive on Linux

```

- [x] sudo apt-get install hfsprogs
- [x] Mount volume

or

- [x] chmod -R 777 /user/media/volumeX

# df -h
# sudo mount -t hfsplus -o remount,force,rw /dev/sdg1
```

## [Remote access using the xrdp package](https://serverspace.io/support/help/install-xrdp-server-on-ubuntu-20-04/)

```
apt install xrdp
adduser xrdp ssl-cert
systemctl restart xrdp

# Allow firewall access on port 3389
ufw allow 3389

# Change "allowed_users" to anybody
# like this: allowed_users=anybody
vim /etc/X11/Xwrapper.config


# Check your hostname
cat /etc/hostname

# Or get your ip address
if config
```

## Install Postman

```
sudo apt update
sudo apt install snapd
sudo snap install postman
```

## Unzip with the destination folder

Set **-d** parameter&#x20;

```
unzip package.zip -d /opt
```

## How to Install netstat Command in Linux

```
# [On CentOS/RHEL]
yum install net-tools     

# [On Debian/Ubuntu]
apt install net-tools     

# [On OpenSuse]
zypper install net-tools  

# [On Arch Linux]
pacman -S netstat-nat     
```

```
netstat -r -n
```

## Show subnet

```
ip -o -f inet addr show | awk '/scope global/ {print $2, $4}'
```

## Show gateway

```
ip route | grep default
```

## User & Groups

### Create new user

```
sudo adduser newuser
```

### Add an existing user to the Sudo group&#x20;

```
sudo usermod -aG sudo newuser
```

### Bluetooth device disconnects right after connect&#x20;

1. Remove the device on Pulse Audio Bluetooth Devices
2. Kill pulse audio and restart the Bluetooth service

```bash
sudo killall pulseaudio && sudo service bluetooth restart
```
