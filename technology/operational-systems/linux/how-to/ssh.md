# SSH

## Disable SSH timeout

```text
sudo vim /etc/ssh/sshd_config
```

Set these options as the followings:

```text
TCPKeepAlive no 
ClientAliveInterval 3200
ClientAliveCountMax 30
```

Restart SSH system service

```text
sudo systemctl restart ssh 
# or sudo /etc/init.d/ssh restart
```

## Increase SSH connection

```text
$ vim ~/.ssh/config

# Content below
Host *
  ServerAliveInterval 240
```

