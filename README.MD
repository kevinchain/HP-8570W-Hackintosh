# HP 8570W Hackintosh

This repo includes an OpenCore EFI for 8570W.


### EFI Compatibility list:

| GPU | Display | Supported? |
| :-----: | :-----: | :-----: |
| NVIDIA | TN-Panel | Yes |
| NVIDIA | DreamColor | No internal display, only external |
| AMD | DreamColor | Yes |


Tested on:

Model | HP Elitebook 8570W
--- | ---
CPU | Intel Core i7-3720QM
GPU | NVIDIA Quadro K1000M
RAM | 16GB DDR3 1600Mhz
Storage | HP SSD 8700 250GB
WiFi & Bluetooth | Azureware AW-CE123H (BCM94352HMB)
Display | TN-Panel
Software | macOS 10.15.5 Catalina

## What works?

- Boot
- GPU acceleration
- Ethernet
- Keyboard + Trackpad (partially)
- WiFi (incl. Handoff + AirDrop)
- Audio

## What doesn't work?

- Battery readout
- Power Management
- Since the 8570W does not have an iGPU and this laptop only has a K1000M, there is no brightness control.
- Trackpad is not being recognised as a Trackpad + no Magic TrackPad 2 Emulation (scrolling works)
- SD-Card

## Download and Install

Copy the EFI folder to your EFI partition... That's it.

## How to Install macOS Catalina

There are two ways you can install Catalina:

1. Have a working install of macOS, download the Installer from the App Store, then make a bootable Installer with createinstallmedia by using this command in Terminal `sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`

2. If you are using Windows, use [macrecovery.py](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/winblows-install.html) from the offical OpenCore release package.

After you have created a bootable Installer, copy the EFI folder to the EFI partition and install as usual. After the installation, mount the EFI partition of the installed OS and copy the EFI folder to its partition.

If you have the original Intel Centrino Wireless-N 6205 card:
You need remove the broadcom kexts and replace them with [Airportitlwm](https://github.com/OpenIntelWireless/itlwm/releases/tag/v1.2.0) and [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases/tag/1.1.2) to get both WiFi and Bluetooth working. But for the full macOS experience with AirDrop, Handoff and all of that, replace the Intel WiFi card.

## Credits

Thanks to:

- me (for wasting my time writing this, providing fixes and creating this EFI)
- acidanthera (for making an awesome bootloader)
- Rehabman (for fixing keyboard issues and providing patches for 8x70)
- [TECHNIKVERBOT](https://github.com/TECHNIKVERBOT) (for the idea to do this because there were no downloads outside of China :P)
- [HansHubertHass](https://github.com/HansHubertHass) (for testing this on his 8570W and buying some hardware so we can resume development again)