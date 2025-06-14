<img align="right" src="https://github.com/woa-miatoll/Port-Windows-11-Redmi-Note-9-Pro/blob/main/Miatoll.png" width="350" alt="Windows 11 Running On A Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro">

# Windows on the Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro

## Dualbooting Android and Windows seamlessly

### Prerequisites
- [```UEFI image```](https://github.com/woa-miatoll/Miatoll-Releases/releases/latest)

- [```WOA Helper app```](https://github.com/n00b69/woa-helper/releases/tag/APK)

## Setting up the dualboot app
> This guide assumes you are rooted, if you aren't, do this first.

### Setup - Android
- Download and install the **WOA Helper** app, then open it and grant it root access.
- Download the **UEFI image** and place it inside the folder named `UEFI` in your internal storage.
- Open the WOA Helper app and use the **STA CREATOR** in **WOA TOOLBOX**.
> [!Important]
> If mounting does not work, go to preferences (the ⚙️ icon) and select `Mount to /mnt instead of /sdcard`
>
> If mounting still does not work, your rom does not support mounting and you will have to make a boot.img backup inside the app, then copy it manually to Windows once you boot to it (for example by uploading it somewhere and then downloading it while booted into Windows). The same applies to the StA files, which are also generated in your internal storage.
>
> Do the same thing if the folder is read-only.
- Press the **QUICKBOOT TO WINDOWS** button.

### Setup - Windows
> [!Tip]
> If this is your first time booting Windows and you wish to skip the Microsoft Account login, press the **I don't have internet** button in the WiFi page, then when prompted, press the **Continue with limited setup** button.
>
> If there is no such button, press the **SIM card** button at the top of the screen (the one that says **Connected**), and press **Disconnect**.
- Navigate to `C:\sta` and create a shortcut of **sta.exe** to your desktop, if one isn't already present
> [!Tip]
> If you are worried about the battery draining in Windows and soft bricking your device, run the **AutoFlash.cmd** located in `C:\sta` which will create a task in **Task Scheduler** that will automatically flash the Android boot.img whenever Windows starts.

#### Booting to Android
- Run the new shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access)

#### Booting to Windows
- Press **QUICKBOOT TO WINDOWS** inside the app, or use the newly created toggle in your quick settings panel

> [!Important]
> If you ever update or change your Android ROM, make sure to create a new **boot.img** backup (after rooting your phone!) and place it inside the **C:\ folder** in Windows, overwriting the old file.
>
> You can use the **BACK UP BOOT IMAGE** feature in the WOA Helper app to do so.

## Finished!