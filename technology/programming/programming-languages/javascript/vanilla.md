# Vanilla

## Clone node by template

```
var myMainBlock = document.getElementById("myMainBlock");
var template = document.querySelector("#template");
var clonedItem = template.cloneNode(true);


clonedItem.removeAttribute("id");
myMainBlock.appendChild(clonedItem);
```
