# Testing Catalina on a Gigabyte B450M DS3H (rev. 1.0)

## Disclaimer

The following files located in this repository are only for **testing** purposes, do not use them for commercial or enterprise applications.

## Hardware used in this test

- Motherboard: Gigabyte B450M DS3H (rev. 1.0)
- CPU: AMD Ryzen 5 2600
- RAM: Pioneer DDR4 2666 - `2 x 8GB`
- SSD: WD Green 120GB
- Graphics Card: Radeon RX560 4GB

## Connections

- DELL Screen plugged to DVI port
- USB Pen Installer, USB Mouse and Keyboard plugged to BLUE USB3 Ports

## BIOS Settings

- BIOS -> Security Option -> System
- BIOS -> Fast Boot -> Disabled
- BIOS -> CSM Support -> Enabled
- BIOS -> Storage Boot OptionControl -> UEFI Only
- BIOS -> Other PCI Device ROM Priority -> UEFI Only

- PERIPHERALS -> Above 4G Decoding -> Enabled
- PERIPHERALS -> Trusted Computing -> Security Device Support -> Disabled
- PERIPHERALS -> Super IO Configuration -> Serial Port 1 -> Disabled
- PERIPHERALS -> USB Configuration -> Legacy USB Support -> Auto
- PERIPHERALS -> USB Configuration -> XHCI Hand-off -> Enabled

- CHIPSET -> IOMMU -> Disabled
- CHIPSET -> SATA MODE -> AHCI

## Windows - USB Installer Preparation

Follow exactly all the steps inside this great website to generate a bootable Catalina Installer. During the preparation, it will be asked to select the version of the OS that you pretend to install. In my case, I selected **Catalina 10.15.4 Full Install**. **If another version is selected, I can not guarantee that will work with the supplied EFI.**
[Windows Install](https://khronokernel-2.gitbook.io/opencore-vanilla-desktop-guide/opencore-efi/winblows-install)

After the USB pen preparation, navigate into the EFI folder located inside the USB installer, delete all the content and replace it with the EFI folder tested by myself.

```sh
EFI_NO_AUDIO Folder - EFI without Audio configured
EFI_WITH_AUDIO Folder - EFI with Audio pre-configured
```

I provide two EFI folders, where the only difference is the Audio, one with Audio disabled and another one with the Audio enabled following the hardware that I have. I only enabled the Audio onboard later following the suggestions indicated inside the OpenCore Guide, but I think if you use exactly the same mob, I don't see any need to make this step later.

## Post-Install

If everything went well, now is the time to make your SSD bootable without the USB Pen. For that final step, follow the guide available by OpenCore. [Booting without USB](https://khronokernel-2.gitbook.io/opencore-vanilla-desktop-guide/post-install/post-install/oc2hdd)

In my case, I just used the Utility provided by Clover, the Clover Configurator, to mount the SSD EFI folder, remove the Apple folder, if exists and copy the BOOT and OC folders from the USB Installer.
