# Known issues

``

## `Type '{}' is not assignable to type 'ReactNode'`

Error example:

```
Erro: ReactNode' is not assignable to type 'React.ReactNode'. Type '{}' is not assignable to type 'ReactNodeReactNode' is not assignable to type 'React.ReactNode'. Type '{}' is not assignable to type 'ReactNode'
```

For those who have this type of error in the APP, just add this item to `resolutions` in the `package.json` file and run a `preinstall` script:

### Solution

* Add the items below inside `package.json`

```
"resolutions": {
    .....
    "@types/react": "^17.0.38"
    ....
  },


"scripts": {
    ......
    "preinstall": "yarn --package-lock-only --ignore-scripts"
    ......
  },
```

* Execute:

```
yarn preinstall
yarn
```
