# How To

## Disable Nginx at startup

```text
sudo systemctl disable nginx
```

## NGiNX Configuration for Vue-Router in HTML5 Mode

{% code title="" %}
```text
server {
  listen 80 default_server;
  listen [::]:80 default_server;

  root /your/root/path;

  index index.html;

  server_name you.server.com;

  location / {
    try_files $uri $uri/ @rewrites;
  }

  location @rewrites {
    rewrite ^(.+)$ /index.html last;
  }

  location ~* \.(?:ico|css|js|gif|jpe?g|png)$ {
    # Some basic cache-control for static files to be sent to the browser
    expires max;
    add_header Pragma public;
    add_header Cache-Control "public, must-revalidate, proxy-revalidate";
  }

}
```
{% endcode %}

