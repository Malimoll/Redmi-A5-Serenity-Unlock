# Magisk 30.6 Root

## Метод

Root получен через патч оригинального stock `init_boot.img` в Magisk.

Исходный stock `init_boot.img`:

```text
C:\Users\Administrator\Desktop\RedmiA5\init_boot.img
```

Размер:

```text
8,388,608 bytes
```

Magisk:

```text
30.6
```

После патчинга изменённый `init_boot` был записан в:

```text
init_boot_b
```

## Проверка root

Команда:

```bat
.\adb.exe shell su -c "id"
```

вернула:

```text
uid=0(root)
```

Контекст:

```text
u:r:magisk:s0
```

Это является фактическим подтверждением работающего root на проверенной конфигурации.

## Почему использовался stock init_boot

Для этой конфигурации был выбран оригинальный stock `init_boot`, а не случайный образ из другого ROM.

Это снижает риск несовместимости ramdisk/kernel-конфигурации.

## Резервная копия

Оригинальный `init_boot.img` сохранён до патчинга.

Не удаляйте его: он нужен для возврата к исходному состоянию соответствующего раздела.
