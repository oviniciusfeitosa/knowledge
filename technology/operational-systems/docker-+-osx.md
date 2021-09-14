# Docker + OSX

## Initial setup for Debian

```text
# install
sudo apt install qemu qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils virt-manager
sudo systemctl enable --now libvirtd
sudo systemctl enable --now virtlogd

echo 1 | sudo tee /sys/module/kvm/parameters/ignore_msrs

sudo modprobe kvm

#add yourself to groups
sudo usermod -aG docker "${USER}"
sudo usermod -aG libvirt "${USER}"
sudo usermod -aG kvm "${USER}"

reboot

# PulseAudio
docker run \\
    --device /dev/kvm \\
    -e AUDIO_DRIVER=pa,server=unix:/tmp/pulseaudio.socket \\
    -v "/run/user/$(id -u)/pulse/native:/tmp/pulseaudio.socket" \\
    -v /tmp/.X11-unix:/tmp/.X11-unix \\
    sickcodes/docker-osx

# start
 docker start $(docker ps -q --all --filter "ancestor=docker-osx")
```

* [https://github.com/vinnyfs89/Docker-OSX\#container-creation-examples](https://github.com/vinnyfs89/Docker-OSX#container-creation-examples)

### References

* [https://github.com/vinnyfs89/Docker-OSX\#initial-setup](https://github.com/vinnyfs89/Docker-OSX#initial-setup)
* [https://www.youtube.com/watch?v=XMj5FY4NXyI](https://www.youtube.com/watch?v=XMj5FY4NXyI)

