<img align="right" src="https://github.com/woa-miatoll/Port-Windows-11-Redmi-Note-9-Pro/blob/main/Miatoll.png" width="350" alt="Windows 11 Running On A Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro">

# Windows на Redmi Note 9 Pro / 9 Pro India / 10 Lite / 9S / 9 Pro max India / Poco M2 Pro

## Выключение Secureboot
> [!Important]
> Следуйте этому гайду, только если вы хотите отключить secureboot

### Требования
- ```Мозги (Очень важно)```

- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)

- [```UEFI```](https://github.com/woa-miatoll/Miatoll-Releases/releases/latest)
## Плюсы и минусы secureboot
> По умолчанию secureboot включен в этом гайде.

##### Плюсы и минусы secureboot
- √ Отсутствие водяного знака на домашнем экране
- √ Приложения, которые не работают в тестовом режиме, будут работать
- √ Вы можете обновить большие версии (например, 22h2 до 23h2) в обновлении Windows напрямую
- × Вы не можете установить неподписанные драйверы

##### Плюсы и минусы отключения secureboot
- √ Вы можете устанавливать неподписанные драйверы
- × Водяной знак тестового режима на домашнем экране
- × Некоторые приложения/игры с анти-читерским ПО могут не работать
- × Вы не сможете обновить большие версии (например, с 22h2 до 23h2) через Windows Update

## Выключение Secureboot

### Перезагрузитесь в рекавери
> Перезагрузите телефон в рекавери

#### Выполните скрипт msc
```cmd
adb shell msc
```

#### Запустите Diskpart
```cmd
diskpart
```

#### Выберите раздел ESP
> Используйте `list volume`, чтобы найти его, замените **$** на номер тома  **ESPMIATOLL**.
```diskpart
select volume $
```

#### Назначьте букву Y
```diskpart
assign letter y
```

#### Выйдите из diskpart
```diskpart
exit
```

#### Измените файлы загрузчика
>Чтобы включить тестовую подпись
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Удаление SiPolicy
> Предполагается, что вы отключаете secureboot на существующей установке, вам нужно удалить этот файл, иначе система не загрузится
```cmd
del Y:\EFI\Microsoft\Boot\SiPolicy.p7b
```

#### Перезагрузитесь в fastbootot
```cmd
adb reboot bootloader
```

#### Прошивка UEFI
> Убедитесь, что вы используете UEFI без secureboot с этой страницы, замените `путь\до\uefi.img` на фактический путь к образу UEFI.
```cmd
fastboot flash boot путь\до\uefi.img
```

> [!Important]
> Не забудьте также заменить старый UEFI в папке UEFI во внутреннем хранилище Android, чтобы случайно не прошить его при следующей попытке переключиться на Windows с Android.

#### Перезагрузка в Windows
```cmd
fastboot reboot
```

## Готово!