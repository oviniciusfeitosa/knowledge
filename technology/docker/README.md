# Docker

## Install Docker Community Edition \(docker-ce\)

```text
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get install docker-ce docker-ce-cli containerd.io
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker 
sudo systemctl enable docker
sudo gpasswd -a $USER docker
```

## Remove all non-used docker containers

```text
docker system prune
```

## NGinX + Reverse proxy + LetsEncrypt SSL

docker.compose.yaml

```text
version: '3.5'

services:
  nginx-proxy:
    network_mode: default
    restart: always
    image: jwilder/nginx-proxy
    container_name: nginx-proxy
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - html:/usr/share/nginx/html
      - dhparam:/etc/nginx/dhparam
      - vhost:/etc/nginx/vhost.d
      - certs:/etc/nginx/certs:ro
      - /var/run/docker.sock:/tmp/docker.sock:ro
    labels:
      - "com.github.jrcs.letsencrypt_nginx_proxy_companion.nginx_proxy"

  letsencrypt:
    network_mode: default
    restart: always
    image: jrcs/letsencrypt-nginx-proxy-companion
    container_name: nginx-proxy-lets-encrypt
    depends_on:
      - "nginx-proxy"
    environment:
      - DEFAULT_EMAIL=yourmail@yourmail.com
    volumes:
      - certs:/etc/nginx/certs:rw
      - vhost:/etc/nginx/vhost.d
      - html:/usr/share/nginx/html
      - /var/run/docker.sock:/var/run/docker.sock:ro

volumes:
  certs:
  html:
  vhost:
  dhparam:
```

## Show real-time logs from initialized container

```text
docker logs -f container-name
```

