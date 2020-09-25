# Shell

## Check if file exists

### With "if" statement

```text
FILE=/etc/resolv.conf
if [ -f "$FILE" ]; then
    echo "$FILE exists."
else 
    echo "$FILE does not exist."
fi
```

### With "&&" operator

```text
[ -f /etc/resolv.conf ] && echo "File exists!"
```



