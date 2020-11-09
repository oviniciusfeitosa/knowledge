# Docker Compose

## Install Docker-compose

```text
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

## Improve performance when using volumes

```text
volumes:
 #- ./:/var/www/html
  - type: bind
    source: .
    target: /var/www/html
    consistency: cached
```

## NGinX + Reverse proxy + LetsEncrypt SSL

{% code title="docker.compose.yaml" %}
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
{% endcode %}

## Show real-time logs from service

```text
docker-compose logs -f service-name
```

