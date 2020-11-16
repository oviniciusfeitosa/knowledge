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

## Check open ports of the server

```text
nmap HOST

## Example

nmap google.com
nmap 55.1.22.5.68
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

