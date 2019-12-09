# Overview

Z370 based build using OpenCore to create a stable and fast workstation used for software development and photo & video editing day in and day out. 

# Hardware

- **Motherboard**: Asus Prime Z370A-II 
- **CPU**: Intel i9-9900k
- **RAM**: Crucial Ballistix Sport AT 3200 MHz DDR4 64GB (16GBx4) 
- **Graphics Card**: ASRock Radeon VII 16GB
- **NVMe**: Samsung 970 EVO 1TB, ADATA SX8200Pro 1TB
- **SSD**: Samsung EVO 860 2TB, Samsung EVO 850 1TB, Crucial MX500 (Windows)
- **Power Suppply**: Seasonic Prime 850 Titanium SSR-850TR 850W
- **Case**: Fractal Design Define R6 USB-C Black Brushed
- **Cooler**: Corsair H75 water cooler
- **Bluetooth**: BCM94360CS2
- **Other**: Blackmagic Design DeckLink Mini Recorder 4K PCIe Capture Card

# Installation

## BIOS

Follow the steps in the guides linked below but if you're going with 4 DIMMS and/or 64GB, beware of using XMP. Through much trial and error with different sets of RAM and motherboards (Z370 & Z390), I've found that it's not stable, neither Crucial nor Corsair, even though rated for and containing XMP profiles for 3200mhz, if you're having any crashes or freezes, just set "Ai Tweaker" to Auto (which sets the RAM to 2400mhz). 

## Steps

1. Prepare OpenCore USB: https://khronokernel-2.gitbook.io/opencore-vanilla-desktop-guide/
   1. Follow this easy and excellent guide, use the Coffee Lake section
   2. Pay special attention to the useful Troubleshooting section: https://khronokernel-2.gitbook.io/opencore-vanilla-desktop-guide/troubleshooting/troubleshooting
2. Create Vanilla Installer: https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/
   1. Ignore the Clover sections, we're using OpenCore

## Kexts

* AppleMCEReporterDisabler.kext
* Lilu.kext
* WhateverGreen.kext
* VirtualSMC.kext
* SMCProcessor.kext
* SMCSuperIO.kext
* AppleALC.kext
* IntelMausiEthernet.kext
* USBInjectAll.kext
* AGPMInjector.kext (Post Install)

# Post Installation

* Create AGPMInjector.kext https://github.com/Pavo-IM/AGPMInjector
* Map USB ports: https://github.com/thenephilim13/macOS/tree/master/asus_prime_z370a-ii/usb

## Creds

Thanks to the entire Acidanthera team for the excellent work, nice to see some actual software engineers with a clean workflow contributing massively to this ecosystem. 