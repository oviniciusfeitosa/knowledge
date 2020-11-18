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

