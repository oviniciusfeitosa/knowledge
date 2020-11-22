# NodeJS

## Topics

* \*\*\*\*[**Proxy**](../../../linux/how-to/proxy.md#proxy-for-npm)\*\*\*\*
* \*\*\*\*[**Yarn**](yarn.md)\*\*\*\*

## Install Nodejs 14.x + Yarn

```text
curl -sL https://deb.nodesource.com/setup_14.x | sudo bash - ; \
sudo apt -y install nodejs gcc g++ make ; \
curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -  ; \
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list  ; \
sudo apt update && sudo apt install yarn ; \
yarn
```



