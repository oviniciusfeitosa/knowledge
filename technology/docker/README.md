# Docker

### Remove all non-used docker containers

```text
docker system prune
```

## NGinX + Reverse proxy + LetsEncrypt SSL

docker.compose.yaml

```text
version: '3'

services:

  nginx-proxy:
    image: jwilder/nginx-proxy
    network_mode: bridge
    container_name: nginx-proxy
    restart: always
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - /etc/nginx/certs
      - /etc/nginx/vhost.d
      - /usr/share/nginx/html
      - /var/run/docker.sock:/tmp/docker.sock:ro
        
  nginx-proxy-letsencrypt:
    image: jrcs/letsencrypt-nginx-proxy-companion
    container_name: nginx-proxy-letsencrypt
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
      - /etc/nginx/certs
      - /etc/nginx/vhost.d
      - /usr/share/nginx/html
    environment:
      - DEFAULT_EMAIL=yourmail@yourmail.com
```



