# uConsole Ubuntu

Community Ubuntu images for ClockworkPi uConsole with Raspberry Pi Compute Modules.

## Choose your edition

| Hardware | Edition | Version | Downloads and documentation |
|---|---|---|---|
| Raspberry Pi CM4 | Ubuntu 26.04 console | Public V1 | [CM4 guide](cm4/) · [CM4 release](https://github.com/zyliu-OU/uconsole/releases/tag/cm4-public-v1) |
| Raspberry Pi CM5 | Ubuntu 26.04.1 desktop | Public V1 | [CM5 guide](cm5/) · Image upload pending |

CM4 and CM5 use separate images, documentation folders and release tags. Select the image for your Compute Module.

## Release status

- **CM4:** published as an experimental pre-release. See its release notes for validation and hardware-test limitations.
- **CM5:** the rebuilt public candidate passed offline kernel/module/firmware checks, package-integrity review, fresh-filesystem checks and verified compression/splitting. Fresh SD-card hardware testing is pending; upload is being prepared.

Large images are attached to GitHub Releases. The repository folders contain documentation. The CM5 release will use tag `cm5-public-v1` and title **uConsole Ubuntu 26.04 CM5 — Public V1**.

## Public editions

Each edition creates your administrator account at first boot. No shared username/password, personal network credentials, lab Python environment or tmux autostart is intended to be included. Follow the edition's setup and checksum instructions.

## Sources and maintenance

The CM5 guide describes the retained Rex kernel, firmware support, source/licence materials and kernel-update limitations. CM5 EEPROM is separate hardware state and is not repaired by reflashing an SD card.

These are unofficial community images. Bundled Ubuntu packages, kernels and firmware retain their respective licences.
