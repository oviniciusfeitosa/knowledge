# How to

## Install Docker Community Edition \( DockerCE \)

```text
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get install docker-ce docker-ce-cli containerd.io
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker 
sudo systemctl enable docker
sudo gpasswd -a $USER docker
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

