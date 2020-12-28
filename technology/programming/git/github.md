# Github

## SSH Key

* Generate key

```text
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

* Add private key to ssh-client

```text
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

* Install xclip

```text
sudo apt-get install xclip
```

* Copy generated file to clipboard \(CTRL + C\)

```text
xclip -sel clip < ~/.ssh/id_rsa.pub

# Example of generated key
# ssh-rsa AAAB3NzaC1cy2EAAAAADQABAAACAQDF/x8E3SaF8TuBkd/Wl1SAfdcpZ1x5LIQpyU/T6IKYBh3Ez+MgCg8FDZcS41PTgJmdytlYv56DxBkRMjgLb5LhzlAxDBp2zJ3hyHJe/e+DOspoeLSbDbTXk9zRyG6W9K4ucxAyXXly5+dcjI79plMxAuejtw63FNTJ/EBCvF73RLQUsqGesdjE2h1fLM2hYhvXkjlajDS2YwfTaFXfTkt/T1UVjQm45xQW4uY1QDHjyt6GzeSkVcacpgJeUYVdIzSfUPTW+RGPwU/dUaknLSOkBBG+c1FYYh6m4pT6sT1tmmLtOgCbCciGWslRVy2xgXTx+lCpl8r8aqT8YYxxyHRHiV7/WRmoglF9dI4idaUYDb7gs7MJV/ekGGtQKzzCUrkY6YPJguL4S13GN9dvnmIf0YQCAzmv/SbYweqBOs87HJMs6yjwQ5YdTBEBCCHDBBMnXOagOkg6u8sHEytwjrDhqGTNd6x6/BEq9NHyofw6i8tSlfiUL3fsmndWZqUIDhT6rYS6iNTs6a9oSUbbit11xU+B50Pw9Bg5ygfUIdlYrhxVYE6bBX8yGY4H3ivAD2E0+i1vBzOQkrx14W4PW0P0xyvVn5McBaByC2RbcoOBonTPI8FfRvhxAhKvMwoC/Le/n/LVJDy/93sOJEflXgrSCsgiWO45L4+ftlsZ91+dwQ== viniciusfesil@gmail.com
```

* Open [Github](https://github.com/settings/keys) and Add the ssh key

## Github Shortcuts

```text
Shift + /
```

## Github: Signing commits using GPG \(Ubuntu/Mac\) ![closed\_lock\_with\_key](https://github.githubassets.com/images/icons/emoji/unicode/1f510.png)

{% hint style="info" %}
* Do you have a Github account? 
  * If not, create one.
* **Install the required tools**
* Latest [Git Client](https://git-scm.com/downloads)
{% endhint %}

### Install GPG Tools

```text
# Ubuntu
sudo apt-get install gpa seahorse
# Mac
brew install gpg
```

### Generate a new GPG [key](https://help.github.com/articles/generating-a-new-gpg-key/)

```text
gpg --gen-key
```

### Answer the questions asked

> Note: When asked to enter your email address, ensure that you enter the verified email address for your GitHub account.

### **List generated key**

```text
gpg --list-secret-keys --keyid-format LONG

# Output
# 
# /home/username/.gnupg/secring.gpg
# -------------------------------
# sec   4096R/<COPY_LONG_KEY> 2016-08-11 [expires: 2018-08-11]
# uid                          User Name <user.name@email.com>
# ssb   4096R/62E5B29EEA7145E 2016-08-11
```

* Note down your key `COPY_LONG_KEY` from above
* **Export this \(public\) key to a text file**

```text
gpg --armor --export <PASTE_LONG_KEY_HERE> > gpg-key.txt
```

* The above command will create a new txt file `gpg-key.txt`
* **Add this key to GitHub**
* Login to Github and goto profile [settings](https://github.com/settings/keys)
* Click `New GPG Key` and paste the content of `gpg-key.txt` file then save
* **Tell git client to auto sign your future commits**
* Run this command

```text
gpg --list-keys

# Output
# 
# /home/username/.gnupg/pubring.gpg
# -------------------------------
# pub   4096R/<COPY_SHORT_KEY> 2016-08-11 [expires: 2018-08-11]
# uid                  Your Name <user.name@gmail.com>
# sub   4096R/EB61969F 2016-08-11 [expires: 2017-08-11]
```

* Copy the short key from above and use this in the command below

```text
git config --global user.signingKey <PASTE_SHORT_KEY_HERE>
git config --global commit.gpgsign true
```

* You are done, next time when you commit changes; GPG will ask you the passphrase.

### Make GPG remember your passphrase \(tricky\)

To make it remember your password, you can use `gpg-agent`

Edit your `~/.gnupg/gpg-agent.conf` file and paste these lines

```text
default-cache-ttl 28800
max-cache-ttl 28800
```

{% hint style="info" %}
_28800 seconds means 8 hours_
{% endhint %}

If gpg-agent is not running you can start it with this command

```text
gpg-agent --daemon
```

#### Change your key passphrase

```text
gpg --edit-key <PASTE_YOUR_KEY_ID_HERE>
```

At the gpg prompt type:

```text
passwd
```

Type in the current passphrase when prompted  
Type in the new passphrase twice when prompted  
Type:

```text
save
```

#### Reference Links

* [https://help.github.com/categories/gpg/](https://help.github.com/categories/gpg/)
* [http://nishanttotla.com/blog/signing-git-commits-gpg/](http://nishanttotla.com/blog/signing-git-commits-gpg/)
* [https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work)
* [https://news.ycombinator.com/item?id=7792026](https://news.ycombinator.com/item?id=7792026)
* [https://overflow.no/blog/2016/08/11/signed-commits-with-gpg-git-and-github-on-linux/](https://overflow.no/blog/2016/08/11/signed-commits-with-gpg-git-and-github-on-linux/)
* [http://stackoverflow.com/questions/10161198/is-there-a-way-to-autosign-commits-in-git-with-a-gpg-key](http://stackoverflow.com/questions/10161198/is-there-a-way-to-autosign-commits-in-git-with-a-gpg-key)
* [http://irtfweb.ifa.hawaii.edu/~lockhart/gpg/gpg-cs.html](http://irtfweb.ifa.hawaii.edu/~lockhart/gpg/gpg-cs.html)
* [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)
* [https://medium.com/@timmywil/sign-your-commits-on-github-with-gpg-566f07762a43\#.aovevj80y](https://medium.com/@timmywil/sign-your-commits-on-github-with-gpg-566f07762a43#.aovevj80y)
* [https://blog.erincall.com/p/signing-your-git-commits-with-gpg](https://blog.erincall.com/p/signing-your-git-commits-with-gpg)

