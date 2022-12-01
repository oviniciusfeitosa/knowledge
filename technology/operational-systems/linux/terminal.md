# Terminal

## [Resume (or retake) stopped job in linux](https://unix.stackexchange.com/a/109539/433712)

You can use [`jobs`](http://www.unix.com/man-page/posix/1/jobs/) to list the suspended process. Take the example. Start with a process:

```
$ sleep 3000  
```

Then you suspend the process:

```
^Z
[1]+  Stopped                 sleep 3000
```

You can list the process:

```
$ jobs
[1]+  Stopped                 sleep 3000
```

and bring it back to the foreground:

```
$ fg %1
sleep 3000
```

The `%1` corresponds to the `[1]` listed with the `jobs` command.

## Delete word in front of pointer

```
ALT + d
```
