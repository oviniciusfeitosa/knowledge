# Proxy

## Proxy for APT

* Define the configs below in the file **`/etc/apt/apt.conf`**

```text
Acquire::http::proxy "http://user:pass@host:port/";
Acquire::https::proxy "http://user:pass@host:port/";
Acquire::ftp::Proxy "ftp://user:pass@host:port/";
```

* or define environments inside the file **`etc/profile`**

```text
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

```text
unset http_proxy
unset https_proxy
unset ftp_proxy
unset HTTP_PROXY
unset HTTPS_PROXY
unset FTP_PROXY
```

## Proxy for SSH

```text
$ route -n
$ sudo route add default gw HOST
$ sudo vim /etc/rc.local

    #!bin/bash  
    route add default gw HOST

$ sudo chmod a+x /etc/rc.local
```

## Proxy for NPM

### Verify the configs from NPM Proxy

```text
npm config get proxy
```

### Add Proxy configs for NPM

```text
npm config set proxy http://"user:pass"@host:port
npm config set https-proxy http://"user:pass"@host:port
```

### Remove proxy for NPM

```text
npm config rm proxy
npm config rm https-proxy
```

## Proxy for Docker

Configs for proxy inside Docker Containers.

### **HTTP Proxy**

```text
$ sudo mkdir -p /etc/systemd/system/docker.service.d 
$ sudo vim /etc/systemd/system/docker.service.d/http-proxy.conf


    # Inside http-proxy.conf
    [Service]
    Environment="HTTP_PROXY=http://user:pass@host:port/" "NO_PROXY=localhost, 127.0.0.0/8, ::1"
    
    
$ systemctl daemon-reload
$ sudo service docker restart
```

### **HTTPS Proxy**

```text
$ sudo mkdir -p /etc/systemd/system/docker.service.d 
$ sudo vim /etc/systemd/system/docker.service.d/https-proxy.conf


    # Inside http-proxy.conf
    [Service]
    Environment="HTTP_PROXY=http://user:pass@host:port/" "NO_PROXY=localhost, 127.0.0.0/8, ::1"

$ systemctl daemon-reload
$ sudo service docker restart
```

### Dockerfile

* To use proxy inside Docker images

```text
$ sudo mkdir -p ~/.docker
$ export DOCKER_CONFIG=~/.docker
$ sudo vim ~/.docker/config.json

    {
        "proxies":
        {
            "default":
            {
                "httpProxy": "http://user:pass@host:port",
                "httpsProxy": "https://user:pass@host:port",
                "noProxy": "localhost, 127.0.0.0/8, ::1"
            }
        }
    }
    
$ sudo service docker restart
```

### 

