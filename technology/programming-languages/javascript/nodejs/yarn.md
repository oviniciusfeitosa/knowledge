# Yarn

## Install package globally

```text
yarn global add 


```

## Global

### Command list

```text
# Install package globally
##### Example
##### yarn global add @nestjs/cli
yarn global add packageName

# Displays the location of the yarn bin folder.
yarn global bin

# List installed packages.
yarn global list

# Remove a package that will no longer be used in your current package.
yarn global remove

# Upgrade packages to their latest version based on the specified range.
yarn global upgrade

# Similar to upgrade command, but display the outdated packages before performing any upgrade, allowing the user to select which packages to upgrade.
yarn global upgrade-interactive
```

## Adding the install location to your PATH

```text
export PATH="$(yarn global bin):$PATH"
```

## 

