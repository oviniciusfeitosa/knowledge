# GitlabCI

## Multiline script

```text
script:
  - |
    echo \
        a \
        b \
        c
```

**or**

```text
script:
  - >
    echo
        a
        b
        c
```

