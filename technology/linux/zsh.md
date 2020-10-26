# ZSH

## Install ZSH

```text
sudo apt install zsh 
chsh -s $(which zsh)
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
source ~/.zshrc
```

## Dracula theme

```text
git clone https://github.com/dracula/zsh ~/.oh-my-zsh/themes/dracula
ln -s $ZSH/themes/dracula ~/.oh-my-zsh/themes/dracula.zsh-theme
vim ~/.zshrc
```

## Plugins



```text
...
    
    plugins=(
      git
      sudo
      zsh-autosuggestions
    )
    
...
```

