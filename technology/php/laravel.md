# Laravel

## zsh: command not found laravel

When you install laravel with this command `composer global require laravel/installer` the command  **laravel** still unavailable.

### Solution

* Add the code below at the end of `~/.zshrc`

```text
PATH="$HOME/.config/composer/vendor/bin:$PATH"
```

* Restart your ZSH

```text
source ~/.zshrc

# Then type Laravel

laravel
```

Be happy 👌

