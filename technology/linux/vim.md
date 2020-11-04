# Vim

## Save read-only files

When you can't save a read-only file, the command below can.

```text
:w !sudo tee % >/dev/null
```

### Create a directory and save a read-only file

```text
:w !sudo mkdir ~/test && sudo tee %
```

The output will appear:

```text
W13: Warning: file "test/.file" was created by another program since the last edition
[O]K, (L)oad file:
```

Then press "**O**"

### Create alias

To create an alias for this command put the content below inside **`~/.vimrc`** file:

```text
cnoremap sudow w !sudo tee % >/dev/null
```

To use the new alias, type **`:sudow`** inside Vim editor

