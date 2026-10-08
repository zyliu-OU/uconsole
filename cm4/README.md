# uConsole Ubuntu 26.04 CM4 — Public V1

[Back to editions](../README.md) · [Download CM4 Public V1](https://github.com/zyliu-OU/uconsole/releases/tag/cm4-public-v1)

Unofficial community console image for ClockworkPi uConsole with Raspberry Pi CM4.

### Included
- Ubuntu 26.04 command-line system.
- uConsole kernel 6.12.62-v8+ and hardware support.
- Wi-Fi, Bluetooth and optional SSH.
- First-boot creation of your own administrator account.
- Detailed boot messages.

### Clean public edition
- No preset user account or shared password.
- No bundled lab Python environment.
- No tmux autostart or custom dashboards.
- System Python retained.

### Test status
Offline filesystem and configuration checks passed.
The preceding image was tested on hardware, but this cleaned public V1
has not been boot-tested. Published as an experimental prerelease.

### Installation
1. Download the .img.xz and .sha256 files.
2. Verify with:
   sha256sum -c uconsole-ubuntu-26.04-CM4-public-V1.img.xz.sha256
3. Flash the .img.xz using Raspberry Pi Imager's "Use custom" option.
   Flashing erases the selected SD card.
4. Boot the uConsole and complete account setup on its keyboard.
5. Connect Wi-Fi:
   sudo nmcli --ask device wifi connect "YOUR_SSID"

Automatic expansion to the full SD-card capacity has not been verified.

This release targets CM4, not CM5.
Ubuntu, ClockworkPi and Raspberry Pi do not endorse this community image.
Bundled third-party software and firmware retain their respective licenses.

