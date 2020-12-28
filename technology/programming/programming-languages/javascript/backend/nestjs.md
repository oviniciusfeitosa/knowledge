# NestJS

## Install globally

```text
yarn global add @nestjs/cli
```

## Create a new project

```text
nest new project-name
```

## Get available routes

```text
const availableRoutes: [] = router.stack
    .map(layer => {
      if (layer.route) {
        return {
          route: {
            path: layer.route?.path,
            method: layer.route?.stack[0].method,
          },
        };
      }
    })
    .filter(item => item !== undefined);
```



