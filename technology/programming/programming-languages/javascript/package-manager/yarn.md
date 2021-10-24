# Yarn

## Global

### Path Setup

{% hint style="info" %}
Add the content below inside your profile that may be **`.profile`**, **`.bash_profile`**, **`.bashrc`**, **`.zshrc`**, etc.
{% endhint %}

```
export PATH="$(yarn global bin):$PATH"
```

### Default config file

.eslintrc

### Install package globally

```
yarn global add @nestjs/cli
```

### Install package globally and specifying the directory

```
yarn global add nodemon --prefix /usr/local
```

### Displays the location of the yarn bin folder

```
yarn global bin
```

### List installed packages

```
yarn global list
```

### Remove a package

```
yarn global remove
```

### Upgrade packages

```
yarn global upgrade
```

### Upgrade Interactively

Similar to upgrade command, but display the outdated packages before performing any upgrade, allowing the user to select which packages to upgrade.

```
yarn global upgrade-interactive
```

