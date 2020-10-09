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

...
```
{% endcode %}

### Cache

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

### User

```text
# List users
wp user list --field=ID

# Create User
wp user create bob bob@example.com --role=author

# With root privileges
root@3aa3b756b002:/var/www/html# wp --alow-root user create admin admin@admin.admin --role=administrator --user_pass=Abcd123456

### Success: Created user 12.
### Password: b58moeu@9&Nzg!#FKn1pROU%

# Create User With password
wp user create admin admin@admin.admin --role=administrator --user_pass=Abcd123456

# Delete User
wp user delete 123

# Update User
wp user update 123 --display_name=Mary --user_pass=marypass
```

### Search and Replace

```bash
# Turn your production multisite database into a local dev database
$ wp search-replace example.com example.test 'wp_*options' wp_blogs

$ wp --allow-root search-replace https://local http://local 'wp_*options'

# Bash script: Search/replace production to development url (multisite compatible)
#!/bin/bash
if $(wp --url=http://example.com core is-installed --network); then
    wp search-replace --url=http://example.com 'http://example.com' 'http://example.test' --recurse-objects --network --skip-columns=guid --skip-tables=wp_users
else
    wp search-replace 'http://example.com' 'http://example.test' --recurse-objects --skip-columns=guid --skip-tables=wp_users
fi
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

