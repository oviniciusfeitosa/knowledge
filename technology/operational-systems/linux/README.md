# Linux

## 

## Topics

* \*\*\*\*[**Desktop Environment**](desktop-environment/)\*\*\*\*
* \*\*\*\*[**How to**](how-to/)\*\*\*\*

## Initial Setup

```text
sudo apt install git vim dconf-cli uuid-runtime pulseaudio blueman pavucontrol \
  pip3 install --user powerline-status;
```

## Systemd

### Look to see which processes are taking the most time of the boot process

```text
systemd-analyze blame
systemd-analyze critical-chain
```

### Displays the current services

```text
systemctl
```

### Disable a systemd service

```text
systemctl disable <service>.
```

### Verify services dependencies

```text
systemctl list-dependencies --reverse plymouth-quit-wait.service
```

## [How to add shared libraries to Linux's system library path](https://blog.andrewbeacock.com/2007/10/how-to-add-shared-libraries-to-linuxs.html) **\(.so\)**

### **Ubuntu**

Create a new file in `/etc/ld.so.conf.d/` called `.conf`  
  
Edit the file and add a line per directory of shared libraries \(\*.so files\), it will look something like:

```text
/usr/lib/APPLICATION/lib
```

Reload the list of system-wide library paths:

```text
sudo ldconfig
```

### **Debian**

Edit `/etc/ld.so.conf`  
  
Add a line per directory of shared libraries \(\*.so files\) to the bottom of the file, it will look something like:

```text
/usr/X11R6/lib
/usr/lib/APPLICATION/lib
```

Reload the list of system-wide library paths:

```text
ldconfig
```

If you run your new application it should now work fine without you having to set any LD\_LIBRARY\_PATH environment variables.  
If you still have problems you can obtain a list of the libraries that are on the system path by re-running the `ldconfig` command in verbose mode:

```text
ldconfig -v
```

## Terminal

### Copy/paste to clipboard

```text
sudo apt install xclip
```

* Create alias to commands inside .bashrc or .zshrc

```text
alias tcopy="xclip -selection c"; 
alias tpaste="xclip -selection clipboard -o"
```

* Example

```text
echo -n test | tcopy
```

## Recommended

* [**How to create Bootable windows image on Linux**](https://github.com/slacka/WoeUSB)\*\*\*\*

