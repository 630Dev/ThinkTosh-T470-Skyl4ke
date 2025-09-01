## Hackintosh for ThinkPad T470 laptops with Intel Skylake CPUs

NOTE: This EFI is confirmed to boot MacOS Sonoma 14.0 and MacOS Sequoia 15.3.1, I have not tested Ventura or older. Tahoe Beta also boots but the sound does not work.

## Specs:

OpenCore Version: 1.0.5

RAM: 2x16GB 2133MHz DDR4

SSD: Micron 1100 Sata 256GB

WiFi & Bluetooth: Intel AC-8260

CPU: Intel Core i5-6300U

GPU: Intel HD Graphics 520 (SPOOFED TO HD GRAPHICS 620 SINCE SKYLAKE IGPUS ARE NOT SUPPORTED IN VENTURA+)

Ethernet controller: Intel I219-LM

Audio: Realtek ALC298


## SCREENSHOTS

Running Sonoma:

<img width="1920" height="1080" alt="1756424761810" src="https://github.com/user-attachments/assets/e5cb462b-5c2d-40f0-857e-8ded9935202b" />

Running Sequoia:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b299d3d8-4ed4-44d5-ae65-6043152806da" />


## WHAT'S NOT WORKING?

USB-C data transfer (No idea why but charging and video output works)

Fingerprint reader (Will not work due to T1 emulation being impossible)

Continuity (This is because of Intel wireless cards are not native in MacOS but if you are using a Broadcom card, this should work fine)

## PRE-INSTALL DEPLOYMENT

Grab [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) and generate a serial with the SMBIOS "MacBookPro13,1" (without quotes)

**IF YOU HAVE A BROADCOM CARD:**

Grab AirportBrcmFixup.kext from [here](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Acidanthera/AirportBrcmFixup-v2.1.9-RELEASE.zip) and put it in EFI/OC/Kexts folder, Open the EFI/OC/config.plist file with OCAT or OpenCore Configurator, Go to Kernel > Add and delete AirportItlwm.kext and add AirportBrcmFixup.kext. Then go into DeviceProperties > Add and delete "PciRoot(0x0)/Pci(0x1C,0x6)/Pci(0x0,0x0)" value. After that you can save your config.plist file. 

## POST-INSTALL

**DISABLE HIBERNATION SINCE IT DOES NOT WORK ON HACKINTOSH PROPERLY:**

Open up a terminal window and type the following commands one by one:

```
sudo pmset autopoweroff 0
sudo pmset powernap 0
sudo pmset standby 0
sudo pmset proximitywake 0
sudo pmset tcpkeepalive 0
```
**FIX TRACKPAD RELATED ISSUES:**

Open System Preferences and navigate to the Trackpad tab. from there do the following:

<img width="707" height="619" alt="image" src="https://github.com/user-attachments/assets/b238a72d-808e-41fd-be13-ba7a30a5f558" />


**FIX WIFI ON SEQUOIA:** 

Grab OCLP-Mod from [here](https://github.com/laobamac/OCLP-Mod) and apply root patches for the WiFi to work (Make sure you are connected to the internet with an ethernet cable before you apply root patches) you can skip this step if you have an Intel card and you are using HeliPort + itlwm.kext
## My sincere thanks to

- [Acidanthera](https://github.com/acidanthera)
- [Dortania's OC guide](https://dortania.github.io/OpenCore-Install-Guide/)
- [CorpNewt's tools](https://github.com/corpnewt)
- [nitingaury's EFI made for the T470 with 7th generation Intel CPUs for the ACPI patches](https://github.com/nitingaury/Thinkpad-T470-EFI-Opencore/tree/main)
