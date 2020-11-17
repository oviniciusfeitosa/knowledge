# How to

## Install Docker Community Edition \( DockerCE \)

```text
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common -y ; \
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -  ; \
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" ; \
sudo apt-get install docker-ce docker-ce-cli containerd.io -y ; \
sudo groupadd docker ; \
sudo usermod -aG docker $USER ; \
newgrp docker  ; \
sudo systemctl enable docker ; \
sudo gpasswd -a $USER docker
```

## Uninstall Docker

```text
sudo apt-get remove docker docker-engine docker.io containerd runc
sudo apt-get purge docker-ce docker-ce-cli containerd.io
sudo rm -rf /var/lib/docker
```

## Remove all non-used docker containers

```text
docker system prune
```

## Show real-time logs from the initialized container

```text
docker logs -f container-name
```

## Size of container

```text
docker ps --size
```

## Get running containers 

### Name

```text
docker ps -f status=running --format "{{.Names}}"
```

### JSON

```text
docker ps -f status=running --format "{{json .}}"
```

## Show online/offline containers

```text
#!/bin/sh
list_of_containers="container1 container2container3"
containers=`docker ps -f status=running --format "{{.Names}}"`
for container in $list_of_containers
do
  if echo $containers |grep -q $container
    then  echo "$container online "
  else echo "$container offline"
    #exit 1
  fi
done
exit 0
```



