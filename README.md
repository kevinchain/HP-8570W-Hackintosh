# HP 8570W Hackintosh

[![OpenCore Version](https://img.shields.io/badge/OpenCore-0.6.6-green.svg)](https://github.com/SkyrilHD/HP-8570W-Hackintosh/)
[![GitHub release](https://img.shields.io/github/release/SkyrilHD/HP-8570W-Hackintosh.svg)](https://github.com/SkyrilHD/HP-8570W-Hackintosh/releases/)
[![GitHub issues](https://img.shields.io/github/issues/SkyrilHD/HP-8570W-Hackintosh.svg)](https://github.com/SkyrilHD/HP-8570W-Hackintosh/issues/)

### Before you give this EFI a try, make sure you read [this](https://github.com/SkyrilHD/HP-8570W-Hackintosh/issues/10)!

This repo includes an OpenCore EFI for 8570W.


### EFI Compatibility list:

| GPU | Display | Supported? |
| :-----: | :-----: | :-----: |
| NVIDIA | TN-Panel | **Yes** |
| NVIDIA | DreamColor | _No internal display, only external_ |
| AMD | DreamColor | _Yes_ |

Bold: confirmed working

Italic: not confirmed



Tested on:

| Specs | Laptop 1 ([@HansHubertHass](https://github.com/HansHubertHass)) | Laptop 2 ([@Bautheile](https://github.com/Bautheile)) |
| -- | -- | -- |
| CPU | Intel Core i7-3720QM | Intel Core i7-3840QM |
| GPU | Nvidia Quadro K1000M  | |
| RAM | 16 GB 1600 MHz DDR3  | 32 GB 1600 MHz DDR3 |
| Screen | 1080p TN-Panel  | |
| WiFi & Bluetooth | Azureware AW-CE123H (BCM94352HMB) | BCM943224HMS |
| OS | macOS 10.15.7 Catalina | |
| BIOS | F.31 | F.61 |

## What works?

- Boot
- GPU acceleration
- Ethernet
- Keyboard + Trackpad (incl. Magic TrackPad 2 emulation)
- WiFi (incl. Handoff + AirDrop)
- Audio
- Docking Station (USB + DVI-D)
- ExpressCard

## What doesn't work?

- Battery readout
- Power Management
- (For NVIDIA) Since the 8570W does not have an iGPU and this laptop only has a K1000M, there is no brightness control.
- SD-Card
- Trackpad won't show up in the macOS settings page when there's no battery readout
- TrackPoint
- Docking Station Audio

## Download and Install

Go to the [Releases](https://github.com/SkyrilHD/HP-8570W-Hackintosh/releases/) page of this repo and download the latest release. Then, copy the EFI folder to your EFI partition... That's it.

## How to Install macOS Catalina

There are two ways you can install Catalina:

1. Have a working install of macOS, download the Installer from the App Store, then make a bootable Installer with createinstallmedia by using this command in Terminal `sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`

2. If you are using Windows, use [macrecovery.py](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/winblows-install.html) from the offical OpenCore release package.

After you have created a bootable Installer, copy the EFI folder to the EFI partition and install as usual. After the installation, mount the EFI partition of the installed OS and copy the EFI folder to its partition.

If you have the original Intel Centrino Wireless-N 6205 card:
You need remove the broadcom kexts and replace them with [Airportitlwm](https://github.com/OpenIntelWireless/itlwm/releases/tag/v1.2.0) and [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases/tag/1.1.2) to get both WiFi and Bluetooth working. But for the full macOS experience with AirDrop, Handoff and all of that, replace the Intel WiFi card.

## Generating your own serial

Use GenSMBIOS (https://github.com/corpnewt/GenSMBIOS) to generate a serial for MacBookPro9,1.

Use PlistEdit Pro or any plist editor to manually enter the details in the config where it says "YOUR OWN STUFF HERE" (as shown in photo) (SystemSerialNumber, MLB, and UUID)

![Screenshot 2021-02-21 001529.jpg](https://raw.githubusercontent.com/SkyrilHD/HP-8570W-Hackintosh/10.15_0.6.6/Screenshot%202021-02-21%20001529.jpg)

You should also add your ethernet adapter's MAC address in the ROM section.


## Credits

Thanks to:

- me (for wasting my time writing this, providing fixes and creating this EFI)
- acidanthera (for making an awesome bootloader)
- Rehabman (for fixing keyboard issues and providing patches for 8x70)
- [TECHNIKVERBOT](https://github.com/TECHNIKVERBOT) (for the idea to do this because there were no downloads outside of China :P)
- [HansHubertHass](https://github.com/HansHubertHass) and [Bautheile](https://github.com/Bautheile) (for being our testers)
