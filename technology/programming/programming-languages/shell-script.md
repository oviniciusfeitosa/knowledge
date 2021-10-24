# Shell Script

## File exists

### With the if statement

```
FILE=/etc/resolv.conf
if [ -f "$FILE" ]; then
    echo "$FILE exists."
else 
    echo "$FILE does not exist."
fi
```

### With the "&&" operator

```
[ -f /etc/resolv.conf ] && echo "File exists!"
```

## Folder exists

```
if [ "$(ls -A /tmp)" ]; then
  echo "Exists and is not Empty"
fi

# Or using `-d`

if ! [ -d "/var/www/html" ] || ! [ -d "/var/www/x-html" ]; then
    echo "Folder not found here - ;("
fi
```

### Or not exists

```
if ! [ "$(ls -A /tmp322)" ]; then
  echo "Empty"
else
  echo "Not Empty"
fi
```

## Find differences between foldes

```
diff -q directory-1/ directory-2/
```

## Show ports in use

```
sudo lsof -i -P -n | grep LISTEN
```

### Create alias

Insert the line below to your `~/.zsh.rc`  or  `~/.profile`

```
alias ports="sudo lsof -i -P -n | grep LISTEN"
```

## Cheatsheet of multiple commands

{% hint style="info" %}
```
A; B    # Run A and then B, regardless of success of A
A && B  # Run B if and only if A succeeded
A || B  # Run B if and only if A failed
A &     # Run A in background.
```
{% endhint %}

**Example**

```
mv tmp.file tmp.file2 ; echo 'aa'
mv tmp.file tmp.file2 && echo 'aa'
mv tmp.file tmp.file2 || echo 'aa'
mv tmp.file tmp.file2 &
```

## Read every line from a file

In the example below read every line from a file and do something.

```
while read line; do
  if [ ! -z $line ]; then
   echo "export $line" >> /etc/apache2/envvars
  fi
done <app.env
```

## Log&#x20;

### Basic view of records

```
journalctl
```

To see the logs that the `journald` daemon has collected, use the `journalctl` command
