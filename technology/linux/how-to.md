# How to

## Download files from the cloud

{% hint style="info" %}
* Send content to WeTransfer cloud-like 
* Download using **wget**
{% endhint %}

### Installing Wget

```text
sudo apt install wget
```

### Download a single file

```text
wget https://wordpress.org/latest.zip
```

### Save the Downloaded File Under Different Name <a id="using-wget-command-to-save-the-downloaded-file-under-different-name"></a>

To save the downloaded file under a different name, pass the `-O` option followed by the chosen name.

```text
wget -O latest-wordpress.zip https://wordpress.org/latest.zip
```

### How to Download in Background with Wget  <a id="how-to-download-in-background-with-wget"></a>

To download in the background, use the option `-b` . In the following example, we are downloading the OpenSuse iso file in the background.

```text
wget -b https://download.opensuse.org/tumbleweed/iso/openSUSE-Tumbleweed-DVD-x86_64-Current.iso
```

## Upload Files

### Single file from remote to local

```text
scp remoteuser@remoteserver:/remote/folder/myfile.txt  myfile.txt
```

### Multiple files from local to remote

```text
scp myfile.txt myfile2.txt remoteuser@remoteserver:/remote/folder/
```

### All files from local to remote

```text
scp * remoteuser@remoteserver:/remote/folder/
```

### All files and folders recursively from local to remote

```text
scp -r * remoteuser@remoteserver:/remote/folder/
```

#### References: [Simplified Guide](https://www.simplified.guide/ssh/copy-file)

## Custom DNS 

```text
$ vim  /etc/resolv.conf   

nameserver 8.8.8.8
nameserver 8.8.4.4
```

## Custom DNS servers for /etc/resolv.conf

To define a custom DNS:

* First, install **`resolvconf`** and follow the commands bellow

```bash
sudo apt install resolvconf -y
```

* Put the nameservers from Google inside the file**`/etc/resolvconf/resolv.conf.d/head`**

```bash
sudo sh -c "echo \"nameserver 8.8.8.8
nameserver 8.8.4.4\" >> /etc/resolvconf/resolv.conf.d/head"
```

* Restart resolvconf service

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

## Search inside files recursively 

```text
grep -rli "my-name"
```

## Display Usage in Megabytes and Gigabytes

```text
df -h
```

### Display a Specific File System

```text
df –h /dev/sda2
```

## Show size of folders

```text
sudo du -shc /var/*
```

## Empty trash

```text
rm -rf ~/.local/share/Trash/*
```

## Search and replace inside the file

```text
sed -i 's/SEARCH_REGEX/REPLACEMENT/g' INPUTFILE
```

## Check network ports in use

```text
sudo netstat -tlnp | grep 80
```

## Check opened network ports of the server

```text
nmap HOST

## Example

nmap google.com
nmap 55.1.22.5.68
```

## Open network ports

```text
# Openning 8080 port
 
 sudo iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
```

## Show real-time logs from OS

```text
tail -f /var/log/syslog
```

## Set Global environment

```text
sudo sh -c "echo MY_GLOBAL_ENV_TO_MY_CURRENT_DIR=$(pwd)" >> /etc/environment"
```

## Set local environment

```text
env MY_GLOBAL_ENV_TO_MY_CURRENT_DIR=$(pwd)
```

## Unset local environment

```text
unset MY_GLOBAL_ENV_TO_MY_CURRENT_DIR
```

## Show all service status

```text
sudo service --status-all 
```

## Exec commands at startup

```text

sudo vim /etc/init.d/rc.local

    #!/bin/bash

    #command1
    #command2
    exit 0;

sudo chmod ugo+x /etc/init.d/rc.local

update-rc.d rc.local defaults
```

## Open Firewall ports

To open ports on the firewall, using the **iptables** command is possible specifying the desired port. Using the example below, just replace port **8888** with the desired port.

```text
$ iptables -I INPUT -p tcp --dport 8888 -j ACCEPT
$ iptables -t filter -I FORWARD -i eth2 -o etho -m multiport --dport 8888 -j ACCEPT
```

## Create an alias for shell commands

* Add the script below at end of the file  **`~/.profile`** 

```text
alias hello_world="echo \"Hello World!\""
```

* Then type your alias directly

```text
hello_world
# output: Hello World
```

## Revalidade ca-certificates

```text
sudo apt-get install -y --reinstall ca-certificates
```

## Remove installed PPA repository

Use the "--remove" flag, similar to how the PPA was added:

```text
sudo add-apt-repository --remove ppa:whatever/ppa
```

As a safer alternative, you can install "ppa-purge":

```text
sudo apt-get install ppa-purge
```

And then remove the PPA, downgrading gracefully packages it provided to packages provided by official repositories:

```text
sudo ppa-purge ppa:whatever/ppa
```

Note that this will uninstall packages provided by the PPA, but not those provided by the official repositories. If you want to remove them, you should tell it to apt:

```text
sudo apt-get purge package_name
```

You can also remove PPAs by deleting the .list files from `/etc/apt/sources.list.d` directory.

Last but not least, you can also disable or remove PPAs from the "Software Sources" section in Ubuntu Settings with a few clicks of your mouse \(no terminal needed\).

## Add multi-touch to your Linux distribution

To do it, make sure to do the steps below:

```text
sudo gpasswd -a $USER input
sudo apt install xdotool wmctrl libinput-tools
git clone https://github.com/bulletmark/libinput-gestures
cd libinput-gestures
sudo ./libinput-gestures-setup install
touch ~/.config/libinput-gestures.conf
```

* Paste the content below inside **`~/.config/libinput-gestures.conf`**:

```text
gesture swipe up 3 xdotool key super+Down  
gesture swipe left 3 xdotool key super+Right  
gesture swipe right 3 xdotool key super+Left  
```

* `After that execute the commands below`

```text
libinput-gestures-setup autostart
libinput-gestures-setup start
libinput-gestures-setup restart
```

### References:

* [https://github.com/bulletmark/libinput-gestures](https://github.com/bulletmark/libinput-gestures)
* [https://www.youtube.com/watch?v=ci6YbQGx3c4](https://www.youtube.com/watch?v=ci6YbQGx3c4)

