# Known Issues

## Set Brave as default browser using Linux

```
update-alternatives --config x-www-browser

# Choose your default browser
```

## Set Brave Nightly as default browser using Linux&#x20;

If are you using **Brave Nightly** follow these steps:

```
xdg-mime default brave-browser-nightly.desktop x-scheme-handler/https
xdg-mime default brave-browser-nightly.desktop x-scheme-handler/http
xdg-settings set default-web-browser brave-browser-nightly.desktop
```

Hope it helps ![+1](https://github.githubassets.com/images/icons/emoji/unicode/1f44d.png)

## How to enable 3rd-party cookies in Google Chrome browser

You may have seen messages like this for example: "_Your browser is most likely blocking third-party cookies, required by the Google widget. Unblock third-party cookies and reload the page to access this feature._"

To solve this problem follow the steps below:

1. In the Google Chrome browser, at the top right, click More ![](https://lh3.ggpht.com/N5LLlFszQeMqXo6Z6UF1VXFN4k3UxO8H8ZU3FV8AjUhomHuRCrwUeKMg1BhuFxKwqQ=w18-h18) and then **Settings**.
2. At the bottom, click on **Advanced**.
3. In the **Privacy and Security** section, click **Site settings**\
   [![](https://cloudhq-image-share.s3.amazonaws.com/d738d65010.png)](https://www.cloudhq.net/c/d738d65010)
4. Select **Cookies**\
   [![](https://s3.amazonaws.com/cloudhq-image-share/cf4519c2ec.png)](https://www.cloudhq.net/c/cf4519c2ec)
5. Uncheck the box next to **Block third-party cookies and site data**:\
   [![](https://www.cloudhq.net/c/6efa431491?dl=1)](https://www.cloudhq.net/c/6efa431491)
6.  Alternatively, you can leave “**Block third-party cookies and site data**” enabled and add cloudHQ.net and google.com in the **Allow** list:\


    1. \[\*.]google.com
    2. \[\*.]cloudhq.net

    [![chrome extension](https://s3.amazonaws.com/cloudhq-image-share/9323333cb9.png)](https://www.cloudhq.net/c/9323333cb9)

**References**

* [https://support.cloudhq.net/how-to-enable-3rd-party-cookies-in-google-chrome-browser/](https://support.cloudhq.net/how-to-enable-3rd-party-cookies-in-google-chrome-browser/)
