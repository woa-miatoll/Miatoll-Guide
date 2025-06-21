<img align="right" src="https://github.com/woa-miatoll/Port-Windows-11-Redmi-Note-9-Pro/blob/main/Miatoll.png" width="350" alt="Windows 11 Running On A Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro">

# Windows on the Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro

## Dualbooting Android and Windows seamlessly

### Prerequisites
- [```UEFI image```](https://github.com/woa-miatoll/Miatoll-Releases/releases/latest)

- [```StA```](https://github.com/woa-miatoll/Miatoll-Guide/releases/tag/dualboot)

- [```M3K Helper app```](https://github.com/WaLoVayu/M3K-Helper/releases/latest)

## Setting up the dualboot app
> This guide assumes you are rooted, if you aren't, do this first.

### Setup - Android
- Download and install the **M3K Helper** app, then open it and grant it root access.
- Download the **UEFI image** and place it inside the folder named `UEFI` in your internal storage.
- Press the **Mount Windows** button, then download and move **sta.exe** to the newly created **Windows** folder in your internal storage.

> [!Important]
> If `/sdcard/Windows` is empty, your rom does not support mounting and you will have to make a boot.img backup inside the app, then copy it manually to Windows once you boot to it (for example by uploading it somewhere and then downloading it while booted into Windows). The same applies to the sta file
>
> Do the same thing if the folder is read-only.

- Return to the M3K Helper and press **QuickBoot to Windows**.

### Setup - Windows
> [!Tip]
> If this is your first time booting Windows and you wish to skip the Microsoft Account login, press the **I don't have internet** button in the WiFi page, then when prompted, press the **Continue with limited setup** button.
>
> If there is no such button, press the **SIM card** button at the top of the screen (the one that says **Connected**), and press **Disconnect**.
- Navigate to `C:\` and create a shortcut of **sta.exe** to your desktop

#### Booting to Android
- Run the new shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access)

#### Booting to Windows
- Press **QUICKBOOT TO WINDOWS** inside the app

> [!Important]
> If you ever update or change your Android ROM, make sure to create a new **boot.img** backup (after rooting your phone!) and place it inside `C:\` in Windows, overwriting the old file.
>
> You can also use the **BACKUP Boot** button in the M3K Helper app to do so.

## Finished!