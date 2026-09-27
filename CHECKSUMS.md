# Checksums

## Unlock / bootloader artifacts

### fdl2-cboot.bin

```text
7E047DC508911F02D6D9F56F0FB3CEC1D4067BE55E9FFB3BB65E372B9D3EBDF6
```

### spl-unlock.bin

```text
AA1A8E94FF160592D1CC45521B269E732F37BC2D5DB06C1C2705BEA8AEC5539A
```

### uboot_b_stock.bin

```text
0036CCC123CC118A8BB32574E1ABADC05643797AD709976A5BDC17A24905DCB1
```

### restore-spl.bin

```text
b8c42f1a746fe11ba7a38477f0b7b459c595a8ab573a2b52e1b4566b70eded7c
```

### restore-uboot.bin

```text
24748AE6A7D6C592835BEDF2866D65E11D4FE006EC602E4B1C70B1BA7FDB9DA6
```

## Stock ROM

```text
MD5:
a5218d449417017a9167ec66d1c80950

SHA256:
9ccd32c1560b03c299b9c7c137fd29cc1dcaa8dc08879be8ff7d2f24556f7234
```

## Verified equivalences

- Current ROM SPL `u-boot-spl-16k-emmc-sign.bin` == `restore-spl.bin`
- Current ROM `lk-sign.bin` == `restore-uboot.bin`
- `uboot_b_cboot_readback.bin` SHA256 == `fdl2-cboot.bin`
- `splloader.bin` == `splloader_bak.bin`
- `splloader` backup matched `restore-spl.bin` byte-for-byte

## SPL patch difference

`spl-unlock.bin` and `restore-spl.bin`:

- same size: 67,144 bytes;
- exactly 80 differing bytes;
- differing regions:

```text
0xB150
0xB26C
0xB3BC
0xB3F4
0xB428
```
