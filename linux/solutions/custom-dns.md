# Custom DNS



To define a custom DNS follow this commands bellow

```bash
sudo apt-get install resolvconf
sudo vim /etc/resolvconf/resolv.conf.d/head
  nameserver 8.8.8.8
  nameserver 8.8.4.4
sudo service resolvconf restart
```

