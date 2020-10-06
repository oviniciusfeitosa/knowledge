# Wordpress

## WP CLI

### Install

```text
wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp
# wp --info
```

Open the `.zshrc`file and add the following line to the bottom of the file:

```bash
autoload bashcompinit
bashcompinit
source /home/$USER/wp-completion.bash
```

Then reload your ZSH

```bash
source ~/.zshrc
```

## Docker

Using the repo [vinnyfs89/docker-wordpress](https://github.com/vinnyfs89/docker-wordpress) as reference. Execute the command below to get your wordpress application working.

```bash
docker-compose up
```

{% hint style="info" %}
The application will use 2 services to handle containers. The first to turn on database and second to application.
{% endhint %}

### WordPress: Too Many Redirects Issue when NGINX reverse proxy to Apache

Add this in your _wp-config.php:_

```bash
$_SERVER['HTTPS'] = 'On';
```

