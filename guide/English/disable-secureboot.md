<img align="right" src="https://github.com/woa-miatoll/Port-Windows-11-Redmi-Note-9-Pro/blob/main/Miatoll.png" width="350" alt="Windows 11 Running On A Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro">

# Windows on the Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro

## Disabling secureboot
> [!Important]
> Follow this guide only if you want to disable secureboot.

### Prerequisites
- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)

- [```UEFI```](https://github.com/woa-miatoll/Miatoll-Releases/releases/latest)

- ```Brain (Very important)```

## Pros and cons of secureboot
> By default, secureboot is enabled in this guide

##### Pros and cons of secureboot
- √ No watermark on homescreen
- √ Apps that do not work with Test Mode will work
- √ You can update big versions (e.g 22h2 to 23h2) in Windows update directly
- × You cannot install unsigned drivers

##### Pros and cons of secureboot disabled
- √ You can install unsigned drivers
- × Test mode watermark on homescreen
- × Some apps/games with anti-cheat software may not work
- × You cannot update big versions (e.g 22h2 to 23h2) through Windows Update

## Disabling secureboot

### Reboot phone to recovery
> Reboot phone into recovery

#### Activate mass storage mode script
```cmd
adb shell msc
```

#### Start the Windows disk manager
```cmd
diskpart
```

#### Select the esp volume of the tablet
> Use `list volume` to find it, replace "$" with the actual number of **WINMIATOLL**
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

#### Modify the bootloader files
> To enable test signing
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Removing SiPolicy
> Assuming you are disabling secureboot on an existing install, you need to delete this file or the system will not boot
```cmd
del Y:\EFI\Microsoft\Boot\SiPolicy.p7b
```

#### Reboot to fastboot
```cmd
adb reboot bootloader
```

#### Flashing the UEFI
> Make sure you use the no secureboot UEFI from this page, replace `path\to\uefi.img` with the actual path to the UEFI image
```cmd
fastboot flash boot path\to\uefi.img
```

> [!Important]
> Make sure to also replace your old UEFI in the UEFI folder in your internal storage of Android, so you don't accidentally flash it the next time you try to switch to Windows from Android

#### Reboot to Windows
```cmd
fastboot reboot
```

## Finished!