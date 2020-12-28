# JQuery

## JQuery serialize form fields

```text
var parameters = {};

$("form").serializeArray().map(function(x){
    parameters[x.name] = x.value;
});
```

