# ZSH

## Install ZSH

```text
sudo apt install zsh -y;
chsh -s $(which zsh);
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
source ~/.zshrc
```

## Fonts

\*\*\*\*[**Install Powerline**](https://microhobby.com.br/blog/2020/05/23/how-to-install-powerline-for-bash-wsl-and-native-linux/#install-powerline)\*\*\*\*

1. Install `pip3`:

   ```text
   sudo apt-get install python3-pip
   ```

2. Install `powerline` using `pip3`:

   ```text
   sudo pip3 install powerline-status
   ```

3. Install `powerline` fonts:

   ```text
   sudo apt-get install fonts-powerline
   ```

## Recommended themes

Set `ZSH_THEME="theme-name"` in `~/.zshrc`  for themes below:

* **bira**
* **gnzh**
* **refined**
* **strug**
* **ys**

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

