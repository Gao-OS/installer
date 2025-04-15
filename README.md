# GaoOS Installer

Download from [Releases](https://github.com/Gao-OS/installer/releases)

## ISO Installer

- Use disko format disk
- use install os use flake

Using minimal cd without GUI, Github Release has a 2GB max size limit.

## Known issue

Nixos can not boot after install.

Fix: use `efibootmgr` fix boot

```shell
sudo efibootmgr -c -L "NixOS-boot" -l "\EFI\NixOS-boot\grubx64.efi" -d /dev/nvme0n1 -p 2
```

### Explain

```shell
sudo efibootmgr -c -L "Label" -l "\EFI\Path\To\Bootloader.efi" -d /dev/sdX -p Y
```

* `-c`: Create a new entry.
* `-L "Label"`: Set the label for the entry.
* `-l "\EFI\Path\To\Bootloader.efi"`: Set the path to the EFI bootloader.
* `-d /dev/sdX`: Set the device where the EFI System Partition (ESP) is located.
* `-p Y`: Set the partition number of the ESP.


# TODO

- [x] ~~Add `aarch64` format ISO Installer~~
- [ ] Add `disk.img.gz` for install to Raspberry PI SD Card 
- [ ] Add AWS EC2 image builder

