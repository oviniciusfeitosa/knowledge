# Laravel

## zsh: command not found laravel

When you install laravel with this command `composer global require laravel/installer` the command  **laravel** still unavailable.

### Solution

* Add `PATH="$HOME/.config/composer/vendor/bin:$PATH"` at end of `~/.zshrc`
* `source ~/.zshrc`
* type `laravel` 

Be happy 👌

