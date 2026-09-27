# Stock ROM, Backups and Restore Notes

## Официальный stock ROM

Использовавшийся ROM:

```text
A15.0.16.0.VGWRUXM
```

Официальный источник Xiaomi:

https://bigota.miui.com/A15.0.16.0.VGWRUXM/serenity_ru_global-images-A15.0.16.0.VGWRUXM-user-20260817.0000.00-15.0-ru-a5218d4494.tgz

Размер:

```text
3,929,047,317 bytes
```

MD5:

```text
a5218d449417017a9167ec66d1c80950
```

SHA256:

```text
9ccd32c1560b03c299b9c7c137fd29cc1dcaa8dc08879be8ff7d2f24556f7234
```

Локальная распакованная папка:

```text
D:/RedmiA5_VGWRUXM_ROM_2026-09-26
```

Полный ROM намеренно не помещён в GitHub: это гигабайты данных. Для воспроизводимости достаточно официальной ссылки и контрольных сумм.

## Резервные копии

Сохранены следующие файлы:

| Файл | Размер |
|---|---:|
| `splloader.bin` | 256 KB |
| `splloader_bak.bin` | 256 KB |
| `uboot_a.bin` | 8 MB |
| `uboot_b.bin` | 8 MB |
| `miscdata.bin` | 1 MB |
| `prodnv.bin` | 64 MB |
| `calinv.bin` | 2 MB |
| `uboot_b_stock.bin` | 8 MB |
| `uboot_b_cboot_readback.bin` | 1,047,272 bytes |
| `init_boot.img` | 8,388,608 bytes |
| `vendor_dlkm_stock.img` | 11,849,728 bytes |
| `mali_kbase_stock.ko` | 2,723,912 bytes |

## Проверенные SHA256

`fdl2-cboot.bin`

```text
7E047DC508911F02D6D9F56F0FB3CEC1D4067BE55E9FFB3BB65E372B9D3EBDF6
```

`spl-unlock.bin`

```text
AA1A8E94FF160592D1CC45521B269E732F37BC2D5DB06C1C2705BEA8AEC5539A
```

`uboot_b_stock.bin`

```text
0036CCC123CC118A8BB32574E1ABADC05643797AD709976A5BDC17A24905DCB1
```

`restore-spl.bin`

```text
b8c42f1a746fe11ba7a38477f0b7b459c595a8ab573a2b52e1b4566b70eded7c
```

`restore-uboot.bin`

```text
24748AE6A7D6C592835BEDF2866D65E11D4FE006EC602E4B1C70B1BA7FDB9DA6
```

## Проверка SPL

`spl-unlock.bin` и `restore-spl.bin` имеют одинаковый размер — 67,144 bytes.

Они отличаются ровно в 80 bytes, в следующих областях:

```text
0xB150
0xB26C
0xB3BC
0xB3F4
0xB428
```

Это было проверено побайтным сравнением.

## Дополнительная проверка

`uboot_b_cboot_readback.bin` имеет SHA256, совпадающий с `fdl2-cboot.bin`.

Оригинальные ROM-файлы SPL и LK также были сравнены с сохранёнными restore-образами.
