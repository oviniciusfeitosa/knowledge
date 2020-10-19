# Docker Compose

## Improve performance when using volumes



```text
volumes:
 #- ./:/var/www/html
  - type: bind
    source: .
    target: /var/www/html
    consistency: cached
```

