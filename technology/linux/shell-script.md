# Shell Script

## File exists

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

## Folder exists

```text
if [ "$(ls -A /tmp)" ]; then
  echo "Exists and is not Empty"
fi

# Or using `-d`

if ! [ -d "/var/www/html" ] || ! [ -d "/var/www/x-html" ]; then
    echo "Folder not found here - ;("
fi
```

### Or not exists

```text
if ! [ "$(ls -A /tmp322)" ]; then
  echo "Empty"
else
  echo "Not Empty"
fi
```

## Find differences between foldes

```text
diff -q directory-1/ directory-2/
```

## Show ports in use

```text
sudo lsof -i -P -n | grep LISTEN
```

### Create alias

Insert the line below to your `~/.zsh.rc`  or  `~/.profile`

```text
alias ports="sudo lsof -i -P -n | grep LISTEN"
```

