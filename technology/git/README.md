# Git

## Push to remote specific branch

Assuming as an example that the remote `upstream` has been added and you need to send code from the local branch `develop` to the remote branch `dev-master`, to be able to execute this operation just execute the command below:

```text
git push upstream develop:dev-master
```

## Reset Permissions

When you accidentally modify the permissions of versioned files, it is possible to return to the initial permission state using the command below

```bash
git diff -p -R --no-ext-diff --no-color \
    | grep -E "^(diff|(old|new) mode)" --color=never  \
    | git apply
```

### Use globally

If you want to use globally, you can do it that way:

```bash
git config --global --add alias.permission-reset '!git diff -p -R --no-ext-diff --no-color | grep -E "^(diff|(old|new) mode)" --color=never | git apply'
git permission-reset
```

## Ignore all files in this folder

{% hint style="info" %}
When you want to ignore files but want to keep a directory you can add a **`.gitignore`** file within the desired directory with the following content
{% endhint %}

```bash
*
!.gitignore
```

## Get current branch

```bash
git branch --show-current
```

## Clear Entire Git Cache

{% hint style="info" %}
To clear your entire Git cache, use the “git rm” command with the “-r” option for recursive
{% endhint %}

```bash
 git rm -r --cached .
```

{% hint style="info" %}
When all files are removed from the index, you can add the regular files back \(the one you did not want to ignore\)
{% endhint %}

```bash
git add .
$ git commit -am 'Removed files from the index (now ignored)'
```

## Cache user and password

```bash
git config credential.helper store
git config --global credential.helper 'cache --timeout 7200'
```

## Stash including untracked files

```bash
git stash --include-untracked
```

