# Known Issues

## Ignores \`Missing file doc comment ...\` errors using PHPCS in VSCode 

You can also use a specific ruleset by adding a `phpcs.xml` to your project. Here's one I'm using in a Laravel project, works in Visual Studio Code with PHPCS extension installed.

```text
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

\*\*\*\*

**References**

* \*\*\*\*[**Github**](https://github.com/squizlabs/PHP_CodeSniffer/issues/1348#issuecomment-581181427)\*\*\*\*

