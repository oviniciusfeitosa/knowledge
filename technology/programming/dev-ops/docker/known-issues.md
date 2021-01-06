# Known issues

## ERROR: Couldn't connect to Docker daemon at http+docker://localunixsocket - is it running?

```text
# Solution
sudo service docker start
```

## docker Err http://deb.debian.org jessie InRelease

* Try to execute the command `nslookup duckduckgo.com 8.8.8.8` . If the message `;; connection timed out; no servers could be reached` appears 
* Then edit your `daemon.json`

```text
# sudo vim /etc/docker/daemon.json

{
    "dns": ["8.8.8.8", "8.8.4.4"]
}
```

* Restart the Docker service

```text
sudo service docker restart
```

