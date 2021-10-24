# Linux

##

## Topics

* ****[**Desktop Environment**](desktop-environment/)****
* ****[**How to**](how-to/)****

## Initial Setup

```
sudo apt install git vim dconf-cli uuid-runtime pulseaudio blueman pavucontrol \
  pip3 install --user powerline-status;
```

## Systemd

### Look to see which processes are taking the most time of the boot process

```
systemd-analyze blame
systemd-analyze critical-chain
```

### Displays the current services

```
systemctl
```

### Disable a systemd service

```
systemctl disable <service>.
```

### Verify services dependencies

```
systemctl list-dependencies --reverse plymouth-quit-wait.service
```

## [How to add shared libraries to Linux's system library path](https://blog.andrewbeacock.com/2007/10/how-to-add-shared-libraries-to-linuxs.html)** (.so)**

### **Ubuntu**

Create a new file in `/etc/ld.so.conf.d/` called `.conf`\
\
Edit the file and add a line per directory of shared libraries (\*.so files), it will look something like:

```
/usr/lib/APPLICATION/lib
```

Reload the list of system-wide library paths:

```
sudo ldconfig
```

### **Debian**

Edit `/etc/ld.so.conf`\
\
Add a line per directory of shared libraries (\*.so files) to the bottom of the file, it will look something like:

```
/usr/X11R6/lib
/usr/lib/APPLICATION/lib
```

Reload the list of system-wide library paths:

```
ldconfig
```

If you run your new application it should now work fine without you having to set any LD\_LIBRARY\_PATH environment variables.\
If you still have problems you can obtain a list of the libraries that are on the system path by re-running the `ldconfig` command in verbose mode:

```
ldconfig -v
```

## Terminal

### Copy/paste to clipboard

```
sudo apt install xclip
```

* Create alias to commands inside .bashrc or .zshrc

```
alias tcopy="xclip -selection c"; 
alias tpaste="xclip -selection clipboard -o"
```

* Example

```
echo -n test | tcopy
```

## Install \`.deb\` files

```
sudo apt install gdebi
sudo gdebi deb-file.deb
```

## Recommended

* [**How to create Bootable windows image on Linux**](https://github.com/slacka/WoeUSB)****
