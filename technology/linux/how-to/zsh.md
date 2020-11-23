# ZSH

## Install ZSH

```text
sudo apt install zsh -y ; \
chsh -s $(which zsh) ; \
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" ; \
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions ; \
source ~/.zshrc
```

## Themes

### [PowerLevel10k](https://github.com/romkatv/powerlevel10k#oh-my-zsh)

```text
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

* Set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc`.
* To configure

```text
p10k configure
```

### Dracula theme

```text
git clone https://github.com/dracula/zsh ~/.oh-my-zsh/themes/dracula ; \
ln -s $ZSH/themes/dracula ~/.oh-my-zsh/themes/dracula.zsh-theme ; \
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

