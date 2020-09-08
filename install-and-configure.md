# Install and configure



`sudo apt install git vim dconf-cli uuid-runtime`

`chsh -s $(which zsh)`

`sudo apt install zsh`

`sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

`git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions`

`source source ~/.zshrc`

`git clone https://github.com/dracula/zsh ~/.oh-my-zsh/themes/dracula.zsh-theme`

`git clone https://github.com/dracula/gnome-terminal ~/www/dracula/gnome-terminal`

`cd ~/www/dracula/gnome-terminal`

`./install.sh`

vim ~/.zshrc

```
...
plugins=(
        git
        sudo
        zsh-autosuggestions
)
```



