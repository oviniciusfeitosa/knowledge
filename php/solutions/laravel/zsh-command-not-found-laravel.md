# zsh: command not found laravel

When you install laravel with this command `composer global require laravel/installer` the command  **laravel** still unavailable.

## ZSH

If you are using ZSH, the solution is:

* Add `PATH="$HOME/.config/composer/vendor/bin:$PATH"` at end of `~/.zshrc`
* `source ~/.zshrc`
* type `laravel` 



Be happy 👌

