# How to

## Push

### Push to a remote specific branch

Assuming as an example that the remote `upstream` has been added and you need to send code from the local branch `develop` to the remote branch `dev-master`, to be able to execute this operation just execute the command below:

```text
git push upstream develop:dev-master
```

### Push ignoring verify or hooks

```text
git push github develop:master --no-verify
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

## Cache

### Clear Entire Git Cache

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

### Cache user and password

```bash
git config credential.helper store
git config --global credential.helper 'cache --timeout 7200'
```

## Stash

### Stash including untracked files

```bash
git stash --include-untracked
```

### Stash only file or folder

```bash
git stash push path/to/file
```

## Revert

### Revert files from a specific hash commit

```bash
git checkout 3df73866bef5d560ef2e5s59b6deaa18001 -- wp-content/uploads/2011 wp-content/uploads/2012 
```

### Revert to a specific commit

```text
git revert --no-commit 0766c053..HEAD
```

## Reset

### Reset Permissions

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

### Reset by time

```bash
git reset --hard master@{"300 minutes ago"}
```

### Undo the last commit

```text
 git reset --soft HEAD~1
```

## Rename

### Rename your branch

```bash
git branch -m new-name
```

If you are on a different branch:

```bash
git branch -m old-name new-name
```

> * Delete the old-name remote branch and push the new-name local branch.
>
> `git push origin :old-name new-name`
>
> * Reset the upstream branch for the new-name local branch.
>
> Switch to the branch and then:
>
> ```text
> git push origin -u new-name
> ```

## Logs

### Find versioned files

To find files that have been versioned, regardless of whether they were removed from versioning or not.

```text
git log --all --full-history -- "**/thefile.*"
```

### View git logs of just one author commits

```text
# Only commits by Vinicius
git log --author="Vinicius"

# Use "--all" to search all branches
git log --author="Vinicius" --all
```

### View git logs of many authors commit

```text
# Many Authors
git log --author="\(Vinicius\)\|\(Jose\)"
```

### Exclude git commits log from one or more author

```text
git log --author='^(?!Vinicius|Jose).*$' --perl-regexp
```

## Proxy bypass to specific host

```text
# Globally
git config --global add remote.{remote_name} proxy 

# Locally
git config --local --add remote.{remote_name}.proxy ""
```

## Fixing wrong commit messages

```text
git rebase -i HEAD~4
```

## Deleting remote branches

```text
git push origin --delete branchName
```

## Keeping a fork up to date

###  Clone your fork:

```text
git clone git@github.com:YOUR-USERNAME/YOUR-FORKED-REPO.git
```

### Add remote from the original repository in your forked repository:

```text
cd into/cloned/fork-repo
git remote add upstream git://github.com/ORIGINAL-DEV-USERNAME/REPO-YOU-FORKED-FROM.git
git fetch upstream
```

### Updating your fork from the original repo to keep up with their changes:

```text
git pull upstream master
```

## How to use prune to Clean Up remote branches <a id="how-to-use-span-classmonospaced-boldprunespan-to-clean-up-remote-branches-in-git"></a>

### Using "prune" on a Remote Repository

The easiest way to use prune is to provide it as an option when fetching:

```text
$ git fetch --prune origin
```

In cases where you'd like to _only_ perform a prune and _not_ fetch remote data, you can use it with the `git remote` command:

```text
$ git remote prune origin
```

If you want to have prune executed with every fetch operation, you can configure Git accordingly:

```text
$ git config --global fetch.prune true
```

## Tags

### Create and tag with a message

```text
git tag -a 0.0.0 -m "initial Changelog" 
```

