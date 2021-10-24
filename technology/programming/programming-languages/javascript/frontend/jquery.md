# JQuery

## JQuery serialize form fields

```
var parameters = {};

$("form").serializeArray().map(function(x){
    parameters[x.name] = x.value;
});
```
