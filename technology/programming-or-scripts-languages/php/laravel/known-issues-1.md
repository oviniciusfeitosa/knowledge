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

