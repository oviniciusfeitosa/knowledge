# Upload to Cloud

## Single file from remote to local

```text
scp remoteuser@remoteserver:/remote/folder/myfile.txt  myfile.txt
```

## Multiple files from local to remote

```text
scp myfile.txt myfile2.txt remoteuser@remoteserver:/remote/folder/
```

## All files from local to remote

```text
scp * remoteuser@remoteserver:/remote/folder/
```

## All files and folders recursively from local to remote

```text
scp -r * remoteuser@remoteserver:/remote/folder/
```



#### References

* [Simplified Guide](https://www.simplified.guide/ssh/copy-file)

