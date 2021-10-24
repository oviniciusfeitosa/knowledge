# Known Issues

## Ignores \`Missing file doc comment ...\` errors using PHPCS in VSCode&#x20;

You can also use a specific ruleset by adding a `phpcs.xml` to your project. Here's one I'm using in a Laravel project, works in Visual Studio Code with PHPCS extension installed.

```
<?xml version="1.0" ?>
<ruleset name="PSR2">
  <description>The PSR2 coding standard.</description>
  <rule ref="PSR2" />
  <file>app/</file>
  <exclude-pattern>vendor</exclude-pattern>
  <exclude-pattern>resources</exclude-pattern>
  <exclude-pattern>database/</exclude-pattern>
  <exclude-pattern>storage/</exclude-pattern>
  <exclude-pattern>node_modules/</exclude-pattern>
</ruleset>
```

**References**

* ****[**Github**](https://github.com/squizlabs/PHP\_CodeSniffer/issues/1348#issuecomment-581181427)****

## **Fatal error: Call to undefined function mcrypt\_module\_open() in {path/file.php} on line yyyyyy" **

### Manual

```
# PHP 5+
apt-get install -y libmcrypt-dev
sudo apt install php5-mcrypt

# PHP 7.x & 8.+
pecl install mcrypt-1.0.3
docker-php-ext-enable mcrypt
```
