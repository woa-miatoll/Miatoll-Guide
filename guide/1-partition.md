<img align="right" src="https://github.com/woa-miatoll/Port-Windows-11-Redmi-Note-9-Pro/blob/main/Miatoll.png" width="350" alt="Windows 11 Running On A Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro">

# Running Windows on the Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro

## Installation

### Prerequisites
- [```Recovery Image```](https://github.com/woa-miatoll/Port-Windows-11-Redmi-Note-9-Pro/releases/tag/Recoveries)

- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)

- ```Brain (Very important)```

### Notes:
> [!Warning]
> All your data will be erased! Back up now if needed.
>
> DO NOT REBOOT YOUR PHONE if you think you made a mistake, ask for help in the [Telegram chat](https://t.me/woamiatoll)
>
> Do not run all commands at once, execute them in order!
>
> **PLEASE DON'T USE OUTDATED VIDEO GUIDES ON YOUTUBE OR ANY OTHER PLATFORM! THESE VIDEOS ARE OUTDATED AND YOU CAN BRICK YOUR DEVICE USING THEM!**

### Opening CMD as an admin
> Download **platform-tools** and extract the folder somewhere, then open CMD as an **administrator**.
>
> It is recommended to keep this window open and use it throughout the entire guide.
>
> Replace `path\to\platform-tools` with the actual path to the platform-tools folder, for example **C:\platform-tools**.
```cmd
cd path\to\platform-tools
```

#### Flash OFOX recovery
> Boot into fastboot mode, then run the following command, replacing `path\to\ofox.img` with the actual path of the image
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

### Partitioning your device
> There are two methods to partition your device. Please select the method you would like to use below.

#### Method 1: Manual partitioning

<details>
  <summary><strong>Click here for method 1</strong></summary>

#### Opening a shell
```cmd
adb shell
```

### Preparing for partitioning
> If at any moment in parted you see an error prompting you to type "Yes/No" or "Ignore/Cancel", type `Yes` or `Ignore` depending on the situation to ignore the errors and continue.
>
> If you see any **udevadm** errors, you can ignore these as well.
```cmd
parted /dev/block/sda
```

#### Printing the current partition table
> Parted will print the list of partitions, userdata should be the last partition in the list
```cmd
print
```

#### Removing userdata
> Replace **$** with the number of the **userdata** partition, which should be **18**
```cmd
rm $
```

#### Recreating userdata
> Replace **10.9GB** with the former start value of **userdata** which we just deleted (it will most likely be 10.9GB)
>
> Replace **70GB** with the end value you want **userdata** to have. In this example your available usable space in Android will be 70GB-10.9GB = **59GB**
```cmd
mkpart userdata ext4 10.9GB 70GB
```

#### Creating ESP partition
> Replace **70GB** with the end value of **userdata**
>
> Replace **70.3GB** with the value you used before, adding **0.3GB** to it
```cmd
mkpart esp fat32 70GB 70.3GB
```

#### Creating Windows partition
> Replace **70.3GB** with the end value of **esp**
```cmd
mkpart win ntfs 70.3GB -0MB
```

#### Making ESP bootable
> Use `print` to see all partitions. Replace "$" with your ESP partition number, which should be **19**
```cmd
set $ esp on
```

#### Exit parted
```cmd
quit
```

### Formatting data
- Format all data in OFOX, or Android will not boot.
- ( Go to Wipe > Format data > type yes )

#### Check if Android still starts
- Just restart the phone, and see if Android still works.
- Set up your device, then go to the next step.

### Formatting Windows and ESP drives
> Reboot into the modded recovery, then run the below command
```cmd
adb shell format
```

</details>

#### Method 2: Automatic partitioning

<details>
  <summary><strong>Click here for method 2</strong></summary>

### Run the partitioning script
```cmd
adb shell
```

- Run the partitioning script `If it asks you to run it once again, do so`

```cmd
partition
```

- Exit adb shell

```cmd
exit
```
### Formatting data

- Format data in OFOX, or Android will not boot.

### Check if Android still starts
- Just restart the phone, and see if Android still works.
- Set up your device, then go to the next step.

</details>

## [Next step: Installing Windows](2-install.md)