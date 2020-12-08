# Chrome / Brave

## Topics

* \*\*\*\*[**Known Issues**](known-issues.md)\*\*\*\*

## Themes

* \*\*\*\*[**GeoMint**](https://chrome.google.com/webstore/detail/geomint/cfanaljjeidpecfgiahmgnokedganpob?hl=pt-BR)\*\*\*\*
* \*\*\*\*[**Minimalism Theme**](https://chrome.google.com/webstore/detail/minimalism-theme/fchfbbbgcmgmoldgikaghpnjbkggbemg?hl=pt-BR)\*\*\*\*
* \*\*\*\*[**Material Dark**](https://chrome.google.com/webstore/detail/material-dark/npadhaijchjemiifipabpmeebeelbmpd?hl=pt-BR)\*\*\*\*
* \*\*\*\*[**Material Incognito Dark Theme**](https://chrome.google.com/webstore/detail/material-incognito-dark-t/ahifcnpnjgbadkjdhagpfjfkmlapfoel?hl=pt-BR)\*\*\*\*
* \*\*\*\*[**Oceanic**](https://chrome.google.com/webstore/detail/oceanic/gbbacdmgjdfajabgglpjifcedoajdimg?hl=pt-BR)\*\*\*\*
* \*\*\*\*[**Material Dark Theme - Space Gray**](https://chrome.google.com/webstore/detail/material-dark-theme-space/hkbfhddllgdpmkmmpofocllfnaeogokm?hl=pt-BR)\*\*\*\*

## Recommended Extensions

* **AdBlock**
* **GoFullPage**
* **Google Tradutor**
* **Grammarly for Chrome**
* **GNOME Shell Integration**
* **JSON Viewer**
* **RSS Feed Reader**
* **The Great Suspender**
* **Video Speed Controller**

## Set Brave as default browser using Linux

```text
update-alternatives --config x-www-browser

# Choose your default browser
```

### Set Brave Nightly as default browser using Linux 

If are you using **Brave Nightly** follow these steps:

```text
sudo xdg-mime default brave-browser-nightly.desktop x-scheme-handler/https
sudo xdg-mime default brave-browser-nightly.desktop x-scheme-handler/http
xdg-settings set default-web-browser brave-browser-nightly.desktop
```

Hope it helps ![+1](https://github.githubassets.com/images/icons/emoji/unicode/1f44d.png)

