# VSCode

## Install VSCode

```text
sudo apt install software-properties-common apt-transport-https wget
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
sudo apt update
sudo apt install code
```

## Activate PowerMode on Visual Studio Code \(VSCode\)

To activate these "blow" effects on the cursor when typing, you will need to **install** PowerMode Plug-in.

[![demo](https://raw.githubusercontent.com/hoovercj/vscode-power-mode/master/images/demo-presets-particles.gif)](https://raw.githubusercontent.com/hoovercj/vscode-power-mode/master/images/demo-presets-particles.gif)

### Visual Studio configs

* Install `Power Mode` plug-in on VSCode Extensions MarketPlace.
* Activate the "**powermode"**

```text
{
    ...
    "powermode.enabled": true,
    "powermode.presets": "flames",
    ...
}
```

* Done!

References: [**Vscode PowerMode Github**](https://github.com/hoovercj/vscode-power-mode)\*\*\*\*

