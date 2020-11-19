# Docker Compose

## Install Docker-compose

```text
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod 777 /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
docker-compose --version
sudo service docker stop
sudo service docker start
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

## NGinX Reverse proxy + LetsEncrypt SSL

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

## Build an image using an external network

```text
version: '3.4'

  service-database:
    user: root
    container_name: vinnyfs89.api-database
    image: 'postgis/postgis:12-3.0'
    ports:
      - '5432:5432'
    volumes:
      - /data/vinnyfs89/api/postgres:/data/postgres:z
      - ./.docker/database:/docker-entrypoint-initdb.d:ro
    env_file:
      - database.env
    networks:
      - vinnyfs89api

  service-server:
    links:
      - 'service-database'
    depends_on:
      - 'service-database'
    container_name: vinnyfs89.api-server
    user: root
    build:
      context: .
      dockerfile: Dockerfile
      network: api_vinnyfs89api
    image: vinnyfs89-api:0.0.1
    volumes:
    #   - .:/usr/src/app
    #   #anonymous volume to prevent the `node_modules` existing in container to be overridden.
    #   - /usr/src/app/node_modules
    command: >
      sh -c "
            npm run migration:run && 
            npm run seed:run &&
            node dist/src/main"
    env_file:
      - .env
    ports:
      - '3000:3000'
    networks:
      - vinnyfs89api

networks:
  vinnyfs89api:
    driver: bridge
    ipam:
      config:
        - subnet: 172.16.57.0/24

```

> **Note**: In order for the "**vinnyfs89api**" network to be visible when building a docker image, the "api\_vinnyfs89api" value needs to be defined using the "**build** &gt; **network**" parameter.

## Docker Compose auto-scale

To specify how many containers to scale using docker-compose use the command **`--scale service = {number}`**. 

```text
# This command sets 5 containers for redis-service
docker-compose up -d --scale redis-service=5

# Example 2
docker-compose -f docker-compose-scale.yml up -d --scale hello=5
```

