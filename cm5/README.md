# uConsole Ubuntu 26.04 CM5 — Public V1

[Back to editions](../README.md)

**Image upload pending.** The local Public V1 candidate has been packaged and verified. Fresh SD-card CM5 hardware testing remains pending. This page will link the separate `cm5-public-v1` release after upload.

## Included support

- Ubuntu 26.04.1 desktop for ClockworkPi uConsole CM5.
- Matched Rex `7.1.4-v8+` kernel, modules, CM5 device tree and display overlays.
- Uncompressed Realtek firmware for USB Wi-Fi/Bluetooth adapter `3625:010b`.
- Speaker amplifier enablement on GPIO11 and retained headphone audio configuration.
- Resumable first-boot administrator account setup; normal desktop password login thereafter.
- First-boot root expansion and visible boot messages.

No administrator account/password is preset. Personal accounts, network credentials, Bluetooth pairings, machine identity, histories and personal dashboards were removed. The distributable image was constructed by copying sanitized live files into freshly created filesystems.

## Validation

Offline checks passed for the selected kernel/modules, device-tree overlay application, firmware bytes and permissions, configured services, provisioning gates, package integrity and targeted privacy checks. Unmounted FAT/ext4 checks passed. The full XZ and its two numbered parts were verified, including reconstruction.

Earlier hardware observations apply to the working source image. This rebuilt candidate has not yet been boot-tested. Root expansion, first-boot recovery, desktop/keyring login and peripheral behavior still require the hardware checklist.

## Download and reconstruct

The planned release title is **uConsole Ubuntu 26.04 CM5 — Public V1**, with tag `cm5-public-v1`. Download both numbered parts and both compressed-image checksum files from that CM5 release when available:

```bash
compressed=uconsole-ubuntu-26.04.1-CM5-public-V1.img.xz
sha256sum -c "$compressed.parts.sha256"
cat "$compressed.part"[0-9][0-9] > "$compressed"
sha256sum -c "$compressed.sha256"
xz -t "$compressed"
```

Use the exact numbered-part glob. A broad `.part*` also matches the parts checksum file.

Use a 16 GB or larger SD card; the image is 9,554,125,312 bytes. Select the intended card in your image-writing application. Use the custom image unchanged, without adding separate Imager account/cloud-init customizations.

## First boot

Allow root expansion to finish. The console on tty1 asks you to create an administrator username and password. Interrupted account setup is designed to resume on the next boot. GDM starts after completed setup; subsequent boots use normal desktop login. Root remains locked and automatic login is disabled.

Connect your own Wi-Fi through the desktop. Bluetooth and the speaker service are enabled. ModemManager is masked; modem/GNSS startup is outside this release's supported configuration.

SSH is opt-in:

```bash
sudo apt update
sudo apt install openssh-server
sudo systemctl unmask ssh.service ssh.socket
sudo ssh-keygen -A
sudo systemctl enable --now ssh.service
```

## Firmware and kernel maintenance

The selected kernel cannot load compressed firmware. Four verified uncompressed Realtek blobs are included. After updating `linux-firmware-realtek`, refresh them with:

```bash
sudo /usr/local/sbin/uconsole-refresh-realtek-firmware
```

Then reboot or reconnect the adapter and retest.

`kernel8.img` selects the matched `7.1.4-v8+` kernel. Raspberry Pi boot-stack packages remain held/pinned to avoid replacing the matched kernel/modules/device-tree set. Ordinary Ubuntu application updates remain available, but the custom kernel does **not** receive Ubuntu stock-kernel security updates automatically. Kernel replacements require maintainer review and CM5 testing.

CM5 EEPROM is separate from the SD-card image. Automatic EEPROM updating is disabled; reflashing this image does not repair EEPROM or guarantee recovery from every boot issue.

## Source and licence materials

The release preparation includes an attribution/source guide, component notices, selected kernel configuration and pinned Rex source archive. The donor changelog identifies commit [03e554ccf8512b1d11bcd0b48621d16d81717541](https://github.com/ak-rex/rpi-linux/commit/03e554ccf8512b1d11bcd0b48621d16d81717541); no bit-for-bit kernel rebuild is claimed.

The source archive is `uconsole-CM5-public-V1-kernel-source.tar.gz`, SHA256:

```text
d979c847f25354074e2e69d1826e20901e2dcafaa6a27d5a34e73b169fe977ea
```

Keep source/configuration and applicable redistribution notices alongside the image. Upstream software and firmware retain their own licences. This repository does not yet assign a reuse licence to new project scripts.

Full documentation and the hardware checklist are bundled inside the image at `/usr/share/doc/uconsole-public-v1/`; release supplements are being prepared for upload.
