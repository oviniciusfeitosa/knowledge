# Proxy

## Proxy for APT

* Define the configs below in the file **`/etc/apt/apt.conf`**

```
Acquire::http::proxy "http://user:pass@host:port/";
Acquire::https::proxy "http://user:pass@host:port/";
Acquire::ftp::Proxy "ftp://user:pass@host:port/";
```

* or define environments inside the file **`etc/profile`**

```
ftp_proxy="http://user:pass@host:port"
http_proxy="http://user:pass@host:port"
https_proxy="https://user:pass@host:port"
FTP_PROXY="http://user:pass@host:port"
HTTP_PROXY="http://user:pass@host:port"
HTTPS_PROXY="https://user:pass@host:port"
HTTP_PROXY_REQUEST_FULLURI="0"
HTTPS_PROXY_REQUEST_FULLURI="0"
```

### To disable Proxy

```
unset http_proxy
unset https_proxy
unset ftp_proxy
unset HTTP_PROXY
unset HTTPS_PROXY
unset FTP_PROXY
```

## Proxy for SSH

```
$ route -n
$ sudo route add default gw HOST
$ sudo vim /etc/rc.local

    #!bin/bash  
    route add default gw HOST

$ sudo chmod a+x /etc/rc.local
```

## Proxy for NPM

### Verify the configs from NPM Proxy

```
npm config get proxy
```

### Add Proxy configs for NPM

```
npm config set proxy http://"user:pass"@host:port
npm config set https-proxy http://"user:pass"@host:port
```

### Remove proxy for NPM

```
npm config rm proxy
npm config rm https-proxy
```

###
