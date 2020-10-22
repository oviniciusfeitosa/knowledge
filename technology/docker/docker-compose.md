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

