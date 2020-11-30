# Yarn

## Global

### Path Setup

{% hint style="info" %}
Add the content below inside your profile that may be **`.profile`**, **`.bash_profile`**, **`.bashrc`**, **`.zshrc`**, etc.
{% endhint %}

```text
export PATH="$(yarn global bin):$PATH"
```

### Default config file

.eslintrc

### Install package globally

```text
yarn global add @nestjs/cli
```

### Install package globally and specifying the directory

```text
yarn global add nodemon --prefix /usr/local
```

### Displays the location of the yarn bin folder

```text
yarn global bin
```

### List installed packages

```text
yarn global list
```

### Remove a package

```text
yarn global remove
```

### Upgrade packages

```text
yarn global upgrade
```

### Upgrade Interactively

Similar to upgrade command, but display the outdated packages before performing any upgrade, allowing the user to select which packages to upgrade.

```text
yarn global upgrade-interactive
```



