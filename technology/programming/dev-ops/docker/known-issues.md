# Known issues

## ERROR: Couldn't connect to Docker daemon at http+docker://localunixsocket - is it running?

```text
# Solution
sudo service docker start
```

## docker Err http://deb.debian.org Jessie InRelease

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

## Docker build “Could not resolve ‘archive.ubuntu.com’” apt-get fails to install anything

{% hint style="info" %}
This doesn't address the underlying issue, but I had success adding **--network=host** to the docker build command.
{% endhint %}

```text
sudo docker build --network=host -t my-docker-image .. 
```

## [By default Docker uses 172.17.0.0/16. This can conflict with the IP range you use for your cloud subnet range](https://support.hyperglance.com/knowledge/changing-the-default-docker-subnet)

By default Docker uses 172.17.0.0/16. This can conflict with the IP range you use for your cloud subnet range

### **Step 1: SSH into the Hyperglance Instance/VM** 

### **Step 2: edit /etc/docker/daemon.json**

You need to add "bip": "172.26.0.1/16" to the JSON in daemon.json

The JSON will look like this after you amend. NOTE remember to add the ',' at the end of the second last '}'.

```text
$ sudo vim /etc/docker/daemon.json

{
  "log-driver": "journald",
  "log-opts": {
    "tag": "{{.Name}}"
  },
  "bip": "172.26.0.1/16"
}

```

### **Step 3: Restart Docker**

```text
sudo systemctl restart docker
```

### **Step 4: Check the routing table**

```text
netstat -rn

# Kernel IP routing table
# Destination Gateway Genmask Flags MSS Window irtt Iface
# 0.0.0.0 172.31.16.1 0.0.0.0 UG 0 0 0 eth0
# 169.254.169.254 0.0.0.0 255.255.255.255 UH 0 0 0 eth0
# 172.18.0.0 0.0.0.0 255.255.0.0 U 0 0 0 br-e9768d205a82
# 172.26.0.0 0.0.0.0 255.255.0.0 U 0 0 0 docker0
# 172.31.16.0 0.0.0.0 255.255.240.0 U 0 0 0 eth0
```

The docker containers will restart and it should then start to collect!

## Could not find an available, non-overlapping IPv4 address pool among the defaults to assign to the network

```text
sudo service network-manager restart
```

Note: when using OpenVPN, **disable** it first.

