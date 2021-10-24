# VSCode

## Install VSCode

```
sudo apt install software-properties-common apt-transport-https wget
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
sudo apt update
sudo apt install code
```

## **Change / Rename all occurrences**

{% hint style="success" %}
Press "**CTRL +  F2**"
{% endhint %}

## Add incrementing numbers for multiple cursors selected

### Solutions

* Wrap with abbreviations: [https://github.com/Microsoft/vscode/issues/62705](https://github.com/Microsoft/vscode/issues/62705)
* Extension: [https://marketplace.visualstudio.com/items?itemName=albymor.increment-selection](https://marketplace.visualstudio.com/items?itemName=albymor.increment-selection)
  * Then: `CTRL + ALT + i`

## Extensions

* **HTML Preview**
