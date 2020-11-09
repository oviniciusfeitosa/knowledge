# Proxy

### Proxy for Docker Images \(Dockerfile\)

To use proxy inside Docker images:

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

## Proxy for Docker Containers

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

### 

