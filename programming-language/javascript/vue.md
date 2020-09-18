# Vue

## VSCode

### Enable "Go to definition" for "@" simbol

To get it done you need to set the content below in your `jsconfig.json` file:

```text
{
  "compilerOptions": {
    "allowSyntheticDefaultImports": true,
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    }
  },
  "include": ["src/**/*"]
}
```

