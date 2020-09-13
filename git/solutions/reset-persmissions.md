# Reset Permissions

### How to

```bash
git diff -p -R --no-ext-diff --no-color \
    | grep -E "^(diff|(old|new) mode)" --color=never  \
    | git apply
```

### Use globally

```bash
git config --global --add alias.permission-reset '!git diff -p -R --no-ext-diff --no-color | grep -E "^(diff|(old|new) mode)" --color=never | git apply'
git permission-reset
```

### References

* [StackOverflow](https://stackoverflow.com/a/4408378)

