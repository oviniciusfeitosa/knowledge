# Composer

## Composer

### Install

```
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
```

### [Make composer vendor/bin folders visible](https://stackoverflow.com/a/46488419)

If your PATH is in **.bashrc** file :

```
echo 'export PATH="$PATH:$HOME/.config/composer/vendor/bin"' >> ~/.bashrc

# Restart your environment
source ~/.bashrc #Bash
```

If your PATH is in **.zshrc** file :

```
echo 'export PATH="$PATH:$HOME/.config/composer/vendor/bin"' >> ~/.zshrc

# Restart your environment
source ~/.zshrc #ZSH
```

## PHPCS&#x20;

### Globally

```bash
  composer global require "squizlabs/php_codesniffer=*"
```

## PHPCS Fixer

### Globally

```bash
 composer global require friendsofphp/php-cs-fixer
```
