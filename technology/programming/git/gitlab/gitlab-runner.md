# Gitlab Runner

## Install

```
curl -L https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh | sudo bash ; \
sudo apt install gitlab-runner -y ; \
sudo mkdir -p /home/gitlab-runner/.config/ ; \
sudo chown -R gitlab-runner: /home/gitlab-runner ; \
sudo chmod -R 777 /home/gitlab-runner/.config/
```

### Add to Docker Group

```
sudo gpasswd -a gitlab-runner docker
sudo service docker stop
sudo service docker start
```

### Register Runner

```
sudo gitlab-runner register

# Example
# url: http://xpto.gitlab.test.com/
# code: FLqz344t90UtBAp_Js1gK
# tag: my-bot-runner
# name: my-bot-runner
# Executor: shell
```

### Start on boot

```
# Check your service
sudo systemctl list-units | grep gitlab
sudo systemctl enable gitlab-runner.service
sudo systemctl start gitlab-runner.service
```

## Commands

```
gitlab-runner start
gitlab-runner restart
gitlab-runner verify
```

## Full permissions

```
sudo usermod -a -G sudo gitlab-runner
```
