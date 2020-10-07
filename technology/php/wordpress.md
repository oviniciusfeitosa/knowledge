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

**Or execute the commands below:**

```bash
echo "autoload bashcompinit" >> ~/.zshrc 
echo "bashcompinit" >> ~/.zshrc 
echo "source /home/$USER/wp-completion.bash" >> ~/.zshrc 
```

Then reload your ZSH

```bash
source ~/.zshrc
```

#### Docker Container + Bash auto-**completion**

{% code title="Dockerfile" %}
```bash
...

RUN wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
RUN chmod +x wp-cli.phar
RUN mv wp-cli.phar /usr/local/bin/wp
RUN echo "source /home/$USER/wp-completion.bash" >> ~/.bashrc 
RUN source ~/.bashrc

...
```
{% endcode %}

### Commands

#### Cache

```bash
  add          Adds a value to the object cache.
  decr         Decrements a value in the object cache.
  delete       Removes a value from the object cache.
  flush        Flushes the object cache.
  get          Gets a value from the object cache.
  incr         Increments a value in the object cache.
  replace      Replaces a value in the object cache, if the value already exists.
  set          Sets a value to the object cache, regardless of whether it already exists.
  type         Attempts to determine which object cache is being used.
  
# Example
  
wp cache flush
```

#### User

```text
# List users
wp user list --field=ID

# Create User
wp user create bob bob@example.com --role=author

### Success: Created user 12.
### Password: b58moeu@9&Nzg!#FKn1pROU%

# Create User With password
wp user create bob bob@example.com --role=administrator --user_pass=marypass

# Delete User
wp user delete 123

# Update User
wp user update 123 --display_name=Mary --user_pass=marypass
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

