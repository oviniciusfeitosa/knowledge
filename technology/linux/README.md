# Linux

## Restart Gnome 3 without closing the programs running

You can use the Gnome Command Box by:

* Press **`Alt+F2`** 
* Type **`r`** 
* Press **`↵`**

👌

## Download files from cloud

* Send content to WeTransfer cloud-like 
* download using **Wget**

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

To download in the background ,use the `-b` option. In the following example, we are downloading the OpenSuse iso file in the background.

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

#### References

* [Simplified Guide](https://www.simplified.guide/ssh/copy-file)

## Custom DNS

To define a custom DNS follow this commands bellow

```bash
sudo apt-get install resolvconf
sudo vim /etc/resolvconf/resolv.conf.d/head
  nameserver 8.8.8.8
  nameserver 8.8.4.4
sudo service resolvconf restart
```

## Get current ip from shell

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

