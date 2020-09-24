# Download from cloud

## How to download files from cloud?

* Send content to cloud like [WeTransfer](https://wetransfer.com/)
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

