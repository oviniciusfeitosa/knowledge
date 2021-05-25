# Shell Script

## File exists

### With the if statement

```text
FILE=/etc/resolv.conf
if [ -f "$FILE" ]; then
    echo "$FILE exists."
else 
    echo "$FILE does not exist."
fi
```

### With the "&&" operator

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

## Cheatsheet of multiple commands

{% hint style="info" %}
```text
A; B    # Run A and then B, regardless of success of A
A && B  # Run B if and only if A succeeded
A || B  # Run B if and only if A failed
A &     # Run A in background.
```
{% endhint %}

**Example**

```text
mv tmp.file tmp.file2 ; echo 'aa'
mv tmp.file tmp.file2 && echo 'aa'
mv tmp.file tmp.file2 || echo 'aa'
mv tmp.file tmp.file2 &
```

## Read every line from a file

In the example below read every line from a file and do something.

```text
while read line; do
  if [ ! -z $line ]; then
   echo "export $line" >> /etc/apache2/envvars
  fi
done <app.env
```

## Log 

### Basic view of records

```text
journalctl
```

To see the logs that the `journald` daemon has collected, use the `journalctl` command

