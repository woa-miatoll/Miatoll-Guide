<img align="right" src="https://github.com/woa-miatoll/Port-Windows-11-Redmi-Note-9-Pro/blob/main/Miatoll.png" width="350" alt="Windows 11 Running On A Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro">

# Running Windows on the Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro

## Installing Windows

### Prerequisites
- [```ARM Windows ESD```](https://arkt-7.github.io/woawin/)

- [```Drivers```](https://github.com/woa-miatoll/Miatoll-Releases/releases/latest)

- ```Brain (Very important)```

### Reboot phone to recovery
> Reboot phone into recovery

#### Execute the msc script
```cmd
adb shell msc
```

### Diskpart
> [!WARNING]
> DO NOT ERASE, CREATE OR OTHERWISE MODIFY ANY PARTITION WHILE IN DISKPART!!!! THIS CAN ERASE ALL OF YOUR UFS OR PREVENT YOU FROM BOOTING TO FASTBOOT!!!! THIS MEANS THAT YOUR DEVICE WILL BE PERMANENTLY BRICKED WITH NO SOLUTION! (except for taking the device to Xiaomi or flashing it with EDL, both of which will likely cost money)
```cmd
diskpart
```

#### Select the Windows volume of the phone
> Use `list volume` to find it, replace "$" with the actual number of **MainOS**
```diskpart
select volume $
```

#### Assign the letter X
```diskpart
assign letter x
```

#### Select the ESP volume of the phone
> Use `list volume` to find it, replace "$" with the actual number of **EFIESP**
```diskpart
select volume $
```

#### Assign the letter Y
```diskpart
assign letter y
```

#### Exit diskpart
```diskpart
exit
```

### Installing Windows
> [!Warning]
> DO NOT USE 24H2!!!

> Replace `path\to\install.esd` with the actual path of install.esd (it may also be named install.wim)
```cmd
dism /apply-image /ImageFile:path\to\install.esd /index:6 /ApplyDir:X:\
```

> If you get `Error 87`, check the index of your image with `dism /get-imageinfo /ImageFile:path\to\install.esd`, then replace `index:6` with the actual index number of Windows 11 Pro in your image

### Installing Drivers
> Unpack the driver archive, then open the `OfflineUpdater.cmd` file

> If it asks you to enter a letter, enter the drive letter of **MainOS** (which should be X), then press enter

#### Create Windows bootloader files
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

### Reboot to Android
```cmd
adb reboot
```

## [Last step: Setting up dualboot](dualboot.md)