# Overview

Z370 based build using OpenCore to create a stable and fast workstation used for software development and photo & video editing day in and day out. 

# Hardware

- **Motherboard**: [Asus Prime Z370A-II](https://smile.amazon.com/gp/product/B07HMGYTVW/)
- **CPU**: [Intel i9-9900k](https://smile.amazon.com/gp/product/B005404P9I/)
- **RAM**: [Crucial Ballistix Sport AT 3200 MHz DDR4 64GB (16GBx4)](https://smile.amazon.com/gp/product/B07M5RMH14) 
- **Graphics Card**: [ASRock Radeon VII 16GB](https://www.newegg.com/asrock-radeon-vii-16g/p/N82E16814930012)
- **NVMe**: Samsung 970 EVO 1TB, ADATA SX8200Pro 1TB
- **SSD**: Samsung EVO 860 2TB, Samsung EVO 850 1TB, Crucial MX500 (Windows)
- **Power Supply**: [Seasonic Prime 850 Titanium SSR-850TR 850W](https://smile.amazon.com/gp/product/B075M3R4YB)
- **Case**: [Fractal Design Define R6 USB-C Black Brushed](https://www.newegg.com/black-fractal-design-define-r6-atx-mid-tower/p/N82E16811352089)
- **Cooler**: [Corsair H75 water cooler](https://smile.amazon.com/gp/product/B00FZHWFEW)
- **Bluetooth**: [BCM94360CS2](https://smile.amazon.com/gp/product/B01L6YWGXW)
- **Bluetooth PCI-E adapter**: [WiFi + Bluetooth 4.0 Card to PCI-E x1 Adapter Card](https://smile.amazon.com/gp/product/B076KBBFV4)
- **Other**: [Blackmagic Design DeckLink Mini Recorder 4K PCIe Capture Card](https://smile.amazon.com/gp/product/B01M126X2N)
- **USB Audio**: [RME ADI-2 Pro fs](https://www.rme-audio.de/adi-2-pro-fs.html)
- **USB Audio**: [Topping DX7s](https://www.amazon.com/Topping-Balanced-Headphone-Amplifier-2ES9038Q2M/dp/B07B4VFS21)

## Bluetooth

Tried many dongles, none worked for me. Make sure you buy the right PCIe adapter card for the bluetooth card, the first one I bought was actually for the BCM94630CD which is NOT compatible with the BCM94360CS2.

Alternative: [Fenvi T919](https://smile.amazon.com/gp/product/B07VCCZS54) no need to buy adapter and card separately, this works great OOB. 

## Audio 

I haven't tested the onboard audio much, so may have to play with the `layout-id` a bit yourself if it's not working 100%. 

# Installation

## BIOS & RAM

Follow the steps in the guides linked below for BIOS settings but if you're going with 4 DIMMS and/or 64GB, beware of using XMP. Through much trial and error with different sets of RAM and motherboards (Z370 & Z390), I've found that it's not stable, neither Crucial nor Corsair, even though rated for and containing XMP profiles for 3200mhz, if you're having any crashes or freezes, just set "Ai Tweaker" to Auto (which sets the RAM to 2400mhz). 

## Steps

1. Prepare OpenCore USB
   1. Follow this easy and excellent guide, use the Coffee Lake section: https://khronokernel-2.gitbook.io/opencore-vanilla-desktop-guide/
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

## Drivers

* VBoxHfs.efi
* VirtualSmc.efi
* ApfsDriverLoader.efi
* FwRuntimeServices.efi
* UsbKbDxe.efi

## Notes 

### Compiling DSL to AML:

1. Open the DSL file with MaciASL
2. Click the Compile button 
3. Check the output and make sure you have no errors
4. File -> Save As: Make sure to select "ACPI Machine Language Binary" as the File Format
5. Copy the binary .aml files to `EC/OC/ACPI` (not the .dsl source files)

### Update config.plist

Make sure to update the `PlatformInfo/Generic` section in the supplied `config.plist` from this repo with your own generated serial etc following the Vanilla Guide. 

### Using XCode to add/edit data fields in plist

Not super intuitive how to add hex data using XCode, for `0xabcdef` enter the following verbatim (make sure the field type is set to `data`): `<abcdef>`

# Post Installation

* Create AGPMInjector.kext https://github.com/Pavo-IM/AGPMInjector
* Map USB ports: https://github.com/thenephilim13/macOS/tree/master/asus_prime_z370a-ii/usb

## Creds

Thanks to the entire Acidanthera team for the excellent work, nice to see some actual software engineers with a clean workflow contributing massively to this ecosystem. 
