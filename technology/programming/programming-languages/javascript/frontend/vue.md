# Vue

### VSCode - Enable "Go to definition" for the "@" symbol

To get it done you need to set the content below in your `jsconfig.json` file:

```
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

## Adding a new property to a reactive object (Vue 2)

```
Vue.set(this.myObject, key, value)
```
