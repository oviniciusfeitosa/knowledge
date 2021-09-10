# Stress Tests

## AB Tool

### Install

```text
sudo apt-get install apache2-dev
# or yum install httpd-tools
```

### How to use

```text
ab -n 9999 -c 333 http://localhost:80/

# 9999 - how many requests
# 333 - how many times
# http://localhost:80/ - host
```

