# SSH

## Disable SSH timeout

```
sudo vim /etc/ssh/sshd_config
```

Set these options as the followings:

```
TCPKeepAlive no 
ClientAliveInterval 3200
ClientAliveCountMax 30
```

Restart SSH system service

```
sudo systemctl restart ssh 
# or sudo /etc/init.d/ssh restart
```

## Increase SSH connection

```
$ vim ~/.ssh/config

# Content below
Host *
  ServerAliveInterval 240
```
