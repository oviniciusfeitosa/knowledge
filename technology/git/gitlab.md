# Gitlab

## Gitlab Runner

### Install

```text
curl -L https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh | sudo bash
sudo apt install gitlab-runner
```

### Config

```text
sudo useradd --comment 'GitLab Runner' --create-home gitlab-runner --shell /bin/bash
#sudo chmod -R 777 /var/lib/gitlab-runner/
#sudo chmod -R 777 /home/gitlab-runner/.config/
sudo gitlab-runner install --user=gitlab-runner --working-directory=/home/gitlab-runner
sudo gitlab-runner start

sudo gitlab-runner restart
sudo gitlab-runner verify

```

### Registrar Runner

```text
sudo gitlab-runner register
```

### Start on boot

```text
# Check your service
systemctl list-units | grep gitlab

systemctl enable gitlab-runner.service
systemctl start gitlab-runner.service
```



