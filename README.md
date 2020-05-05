## Latest Update

* Swapped motherboards between the two systems, main desktop is now using the Z390 (unsure how much I'll maintain the Z370 going forward)
* Gigabyte Aorus Z390 Pro only:
  * Updated to OpenCore 0.5.8
  * Change to `iMac19,1` SMBIOS 
  * Using the OpenCanopy graphical UI boot picker 
  * Using the new `SSDT-PLUG.aml` (supports multiple systems without having to edit)
  * Remove `ApfsDriverLoader.efi` (deprecated, included in OC 0.5.8)
  * Added two USB2.0 ports to existing USB3.0 ports (the two blues ones at the bottom), found that if I plug a USB3.0 hub into one of them and in turn plug in a keyboard & mouse in the hub, they were not working - however the hub is now detected as a USB2.0 hub (with the keyboard & mouse plugged into it)

**TODO**: Enable iGPU and see if slide=0 still holds (more hope now that we have `RebuildAppleMemoryMap` quirk)

## Gigabyte Aorus Z390 Pro with i9-9900k and Radeon VII with OpenCore

[Overview & Installation](gigabyte_z390_aorus_pro/)

## Asus Prime Z370A-II with i7-8700k and Radeon Vega64 with OpenCore

[Overview & Installation](asus_prime_z370a-ii/)

