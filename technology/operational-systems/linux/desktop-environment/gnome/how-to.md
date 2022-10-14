# How to

## Restart Gnome 3 without closing the programs running

You can use the Gnome Command Box by:

* Press **`Alt+F2`**&#x20;
* Type ** `r`**&#x20;
* Press **`↵`**

👌

## Changing the default location path of gnome-screenshot

```
gsettings set org.gnome.gnome-screenshot auto-save-directory "file:///home/$USER/Downloads/"
```

## Uninstall Gnome Shell Extensions

* Move extensions to your user extensions dir

```
sudo mv /usr/share/gnome-shell/extensions/* ~/.local/share/gnome-shell/extensions/
```

* Set right permissions

```
sudo chown -R $(whoami): ~/.local/share/gnome-shell/extensions/
```

* Do this step: [Restart Gnome 3 without closing the programs running](how-to.md#restart-gnome-3-without-closing-the-programs-running)
* Access your installed extensions by gnome-tweak or [Gnome Shell Extensions](https://extensions.gnome.org/local/) site
* Remove what you want

![](<../../../../../.gitbook/assets/image (5).png>)

## Window adjustments

### Open new centralized window

```
gsettings set org.gnome.mutter center-new-windows true 
```

### Center current window

* Install [this](https://extensions.gnome.org/extension/4375/bifocals/) Gnome Shell Extension
* Press **CTRL + Window + M**
