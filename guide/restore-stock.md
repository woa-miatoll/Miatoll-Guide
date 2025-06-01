<img align="right" src="https://github.com/woa-miatoll/Port-Windows-11-Redmi-Note-9-Pro/blob/main/Miatoll.png" width="350" alt="Windows 11 Running On A Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro">


# Running Windows on the Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro

## Uninstallation

### Why is this needed?

If you want to uninstall windows this is used instead of deleting partitions manually to avoid human error + writing a whole dedicated guide to just uninstalling.

If you want to relock your bootloader you'll need your partition table to be stock.

### Prerequisites
- [```ADB & Fastboot```](https://developer.android.com/studio/releases/platform-tools)

- [```gpt_both0.bin```](https://github.com/woa-miatoll/Port-Windows-11-Redmi-Note-9-Pro/releases/tag/Binaries)

### Restore GPT
> Replace ```<gpt_both0.bin>``` with the path to the gpt_both0.bin file.

```cmd
fastboot flash partition:0 <gpt_both0.bin>
```

### Erase userdata to avoid bootloop and restore FS size
```cmd
fastboot -w
```
