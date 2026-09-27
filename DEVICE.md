# Device and Partition Layout

## Hardware

```text
Model:       25028RN03A
Codename:    serenity
Product:     serenity_ru
SoC:         Unisoc T7250 / UMS9230
Storage:     eMMC
Android:     15 Go
```

## A/B

Устройство использует A/B-разметку.

Во время основной части эксперимента активным был слот B.

Проверка выполнялась через fastboot и adb.

## by-name map на B

Критические соответствия, полученные из recovery:

```text
boot       -> boot_b
init_boot  -> init_boot_b
vendor_boot -> vendor_boot_b
uboot      -> uboot_b
spl        -> spl_b
userdata   -> mmcblk0p81
super      -> mmcblk0p48
misc       -> mmcblk0p4
miscdata   -> mmcblk0p2
prodnv     -> mmcblk0p1
calinv     -> mmcblk0p75
dtb        -> dtb_b
dtbo       -> dtbo_b
vbmeta     -> vbmeta_b
```

## Dynamic partitions

Проверка показала:

```text
fastboot getvar is-logical:system_b
```

ответила:

```text
yes
```

То есть `system_b` является logical partition внутри dynamic/super layout.

## Важная особенность stock super

При исследовании stock `super` было обнаружено, что A logical partitions были заполнены, а B entries в stock-образе были пустыми.

Поэтому нельзя автоматически брать stock `super` как готовый источник B-варианта всех logical partitions.

## product_b

Во время установки GSI возникла нехватка места для `system_b`.

Попытки освободить место через snapshot/COW cleanup проблему не решили.

В результате для успешной записи GSI был удалён именно `product_b`.

После этого LineageOS GSI успешно записался и загрузился.

**Не следует без необходимости создавать `product_b` обратно или менять dynamic partition layout.**

## Предупреждение

`super`, `product`, `vendor_dlkm`, `system_dlkm` и другие dynamic partitions связаны с конкретной конфигурацией устройства.

Перед экспериментами сохраняйте состояние, которое можно восстановить из stock ROM.
