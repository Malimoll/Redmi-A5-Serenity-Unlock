# PBRP and LineageOS 22.2 GApps GSI

## PBRP

Использовался PBRP 4.0 UNOFFICIAL.

Источник device tree:

https://github.com/KSN2redawew/android_device_xiaomi_serenity-twrp

PBRP был установлен в:

```text
vendor_boot_b
```

Команда:

```bat
fastboot flash vendor_boot_b PBRP.img
```

После этого выполнялась загрузка в recovery.

## Расшифровка Data

PBRP не смог расшифровать Data обычным PIN.

Это не было поводом форматировать `userdata`.

Форматирование Data в этой сессии не выполнялось только ради исправления ошибки расшифровки.

ADB в PBRP работал:

```text
adb devices
```

показывал устройство в состоянии:

```text
recovery
```

## LineageOS

Использованный GSI:

```text
LineageOS-22.2-20260105-GAPPS-EXT4-GSI.img
```

Размер:

```text
3,340,144,640 bytes
```

Файл использовался в fastbootd.

GSI успешно загрузился после корректировки dynamic partition layout.

## Проблема с размером system_b

Первая попытка flash GSI в `system_b` завершилась из-за недостаточного свободного места.

После удаления `product_b` запись GSI прошла успешно.

Далее устройство загрузило LineageOS и дошло до первоначальной настройки Android.

## Источник community guide

https://github.com/barryC12/LineageOS-PocoC71

Это community material, а не официальный документ Xiaomi.

## Важное предупреждение

Не выполняйте `fastboot -w` и операции с dynamic partitions без понимания последствий: они могут удалить пользовательские данные.

В данной сессии `fastboot -w` был выполнен перед установкой GSI.
