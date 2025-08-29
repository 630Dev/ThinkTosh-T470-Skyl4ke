NOTE: This EFI is confirmed to boot MacOS Sonoma 14.0, however I have not tested newer versions (Sequoia, Tahoe. Ventura should work fine but I have not tested)

**Specs:**

OpenCore Version: 1.0.5

RAM: 2x16GB 2133MHz DDR4

SSD: Micron 1100 Sata 256GB

WiFi & Bluetooth: Intel AC-8260 (I used itlwm.kext since AirportItlwm.kext does not work on Sonoma)

CPU: Intel Core i5-6300U

GPU: Intel HD Graphics 520 (SPOOFED TO HD GRAPHICS 620 SINCE SKYLAKE IGPUS ARE NOT SUPPORTED IN VENTURA+)

Ethernet controller: Intel I219-LM

Audio: Realtek ALC298


**SCREENSHOTS**

<img width="1920" height="1080" alt="1756424761810" src="https://github.com/user-attachments/assets/e5cb462b-5c2d-40f0-857e-8ded9935202b" />



**WHAT'S NOT WORKING?**

USB-C data transfer (No idea why but charging and video output works)

Fingerprint reader (Will not work due to T1 emulation being impossible)

Continuity (This is because of Intel wireless cards are not native in MacOS)

**POST-INSTALL**

Disable hibernation since it doesn't work properly on hackintoshes
```
sudo pmset autopoweroff 0
sudo pmset powernap 0
sudo pmset standby 0
sudo pmset proximitywake 0
sudo pmset tcpkeepalive 0
```
## My sincere thanks to**

- [Acidanthera](https://github.com/acidanthera)
- [Dortania's OC guide](https://dortania.github.io/OpenCore-Install-Guide/)
- [CorpNewt's tools](https://github.com/corpnewt)
- [nitingaury's EFI made for the T470 with 7th generation Intel CPUs for the ACPI patches](https://github.com/nitingaury/Thinkpad-T470-EFI-Opencore/tree/main)
