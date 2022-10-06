# Audio

## PulseAudio - LoopBack

### Manual

```
pactl load-module module-loopback
```

### Automatic

```
# /etc/pulse/default.pa
# As root add the line below:
load-module module-loopback
```
