# Gnome Initial Setup

### Install

#### Basic Stuff

```text
sudo apt install git vim dconf-cli uuid-runtime zsh
```

#### ZSH

```text
sudo apt install zsh chsh -s $(which zsh)
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
source source ~/.zshrc
```

#### Nodejs 14.x + Yarn

```text
curl -sL https://deb.nodesource.com/setup_14.x | sudo bash -
sudo apt -y install nodejs gcc g++ make
curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install yarn
```

#### VSCode

```text
sudo apt install software-properties-common apt-transport-https wget
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
sudo apt update
sudo apt install code
```

### Theming

#### ZSH

```text
git clone https://github.com/dracula/zsh ~/.oh-my-zsh/themes/dracula.zsh-theme
vim ~/.zshrc


    ...
    
    plugins=(
      git
      sudo
      zsh-autosuggestions
    )
    
    ...
```

#### Gnome Terminal

```text
git clone https://github.com/dracula/gnome-terminal ~/www/dracula/gnome-terminal
cd ~/www/dracula/gnome-terminal
./install.sh
```
