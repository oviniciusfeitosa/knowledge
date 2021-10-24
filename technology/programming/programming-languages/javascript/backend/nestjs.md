# NestJS

## Install globally

```
yarn global add @nestjs/cli
```

## Create a new project

```
nest new project-name
```

## Get available routes

```
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

