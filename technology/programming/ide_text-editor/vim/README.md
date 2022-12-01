# Vim

## Save read-only files

When you can't save a read-only file, the command below can.

```
:w !sudo tee % >/dev/null
```

### Create a directory and save a read-only file

```
:w !sudo mkdir ~/test && sudo tee %
```

The output will appear:

```
W13: Warning: file "test/.file" was created by another program since the last edition
[O]K, (L)oad file:
```

Then press "**O**"

### Create alias

To create an alias for this command put the content below inside **`~/.vimrc`** file:

```
cnoremap sudow w !sudo tee % >/dev/null
```

To use the new alias, type **`:sudow`** inside Vim editor

## Set vim as default editor

### Alternative 1:&#x20;

```
sudo update-alternatives --config editor
```

### Alternative 2: Global Context

Set to global context:

```
export VISUAL=vim
export EDITOR="$VISUAL"
```

#### Git

Set core.editor in your Git config:

```
git config --global core.editor "vim"
```

Set the GIT\_EDITOR environment variable:

```
export GIT_EDITOR=vim
```

## Commands

### Deleting words

```
dw  ---> Delete the word from your cursor to the end of the word
diw ---> Delete inside word.
daw ---> Delete all words from your cursor
```

### [Move lines up or down](https://vim.fandom.com/wiki/Moving\_lines\_up\_or\_down#Move\_command)

The following mappings in your [vimrc](https://vim.fandom.com/wiki/Vimrc) provide a quick way to move lines of text up or down. The mappings work in normal, insert and visual modes, allowing you to move the current line, or a selected block of lines.

```
nnoremap <A-j> :m .+1<CR>==
nnoremap <A-k> :m .-2<CR>==
inoremap <A-j> <Esc>:m .+1<CR>==gi
inoremap <A-k> <Esc>:m .-2<CR>==gi
vnoremap <A-j> :m '>+1<CR>gv=gv
vnoremap <A-k> :m '<-2<CR>gv=gv
```

In normal mode or in insert mode, press Alt-j to move the current line down, or press Alt-k to move the current line up.

After visually selecting a block of lines (for example, by pressing `V` then moving the cursor down), press Alt-j to move the whole block down, or press Alt-k to move the block up.
