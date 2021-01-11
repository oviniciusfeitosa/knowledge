# Linux

## Topics

* \*\*\*\*[**Desktop Environment**](desktop-environment/)\*\*\*\*
* \*\*\*\*[**How to**](how-to/)\*\*\*\*

## Initial Setup

```text
sudo apt install git vim dconf-cli uuid-runtime pulseaudio blueman; \
  pip3 install --user powerline-status;
```

## Systemd

### Look to see which processes are taking the most time of the boot process

```text
systemd-analyze blame
systemd-analyze critical-chain
```

### Displays the current services

```text
systemctl
```

### Disable a systemd service

```text
systemctl disable <service>.
```

### Verify services dependencies

```text
systemctl list-dependencies --reverse plymouth-quit-wait.service
```

## Recommended

* [**How to create Bootable windows image on Linux**](https://github.com/slacka/WoeUSB)\*\*\*\*

