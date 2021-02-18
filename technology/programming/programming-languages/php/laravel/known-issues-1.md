# Know Issues

## zsh: command not found laravel

When you install laravel with this command `composer global require laravel/installer` the command **laravel** still unavailable.

### Solution

```text
echo "PATH=\"$HOME/.config/composer/vendor/bin:$PATH\"" >> ~/.zshrc

# Restart your ZSH
source ~/.zshrc
```

Be happy 👌

## tymon/jwt-auth 0.5.12 requires illuminate/support ~5.0 -&gt; found illuminate/support\[v5.0.0, ..., 5.8.x-dev\] but it conflicts with your root composer.json require \(^8.18\).

```bash
composer require tymon/jwt-auth:^1.0.2
```

## flock\(\) expects parameter 1 to be resource, boolean given

* Go to your application root folder
* Give permissions to your `storage`folder

```bash
sudo chmod -R 775 storage
```

