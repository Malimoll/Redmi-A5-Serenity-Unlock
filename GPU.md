# Mali GPU / SystemUI Lag Investigation

## Наблюдение

Во время работы LineageOS видео YouTube могло воспроизводиться плавно, одновременно с чем shell/SystemUI периодически испытывали лаги или зависания.

CPU не выглядел полностью загруженным.

## SystemUI jank

`dumpsys gfxinfo com.android.systemui` показал реальные пропуски кадров.

Зафиксированные примеры:

```text
67 frames / 19 janky
90 frames / 30 janky
185 frames / 39 janky
```

Это подтверждает наличие UI frame jank, но само по себе не доказывает конкретную причину.

## GPU devfreq

Путь:

```text
/sys/class/devfreq/23100000.gpu
```

Доступные частоты:

```text
850000000
768000000
614400000
512000000
384000000
```

Governor:

```text
simple_ondemand
```

Доступные governors включали:

```text
performance
powersave
simple_ondemand
```

## Mali kernel module

Модуль:

```text
mali_kbase
```

Параметры, обнаруженные при исследовании:

```text
gpu_pollingtime = 50
gpu_upthreshold = 40
gpu_downdifferential = 5
gpu_boost_level2 = 0
```

## Попытка live tuning

Прямые записи в governor/min_freq и параметры модуля завершались:

```text
Permission denied
```

даже после получения root.

Также vendor/vendor_dlkm/odm/system_dlkm были read-only (EROFS).

## Debugfs

После изменения SELinux в permissive удалось прочитать Mali debugfs.

В статистике частот GPU преобладало время на:

```text
384 MHz
```

но были подтверждены переходы на максимальную частоту.

В частности, transition statistics содержали:

```text
384 -> 850 MHz : 31
850 -> 384 MHz : 9
```

Таким образом, в проверенной сессии нет основания утверждать, что GPU был навсегда заблокирован на 384 MHz.

## vendor_dlkm

Рабочий vendor_dlkm был сохранён через dd.

Также был извлечён stock:

```text
mali_kbase_stock.ko
```

Размер:

```text
2,723,912 bytes
```

## Экспериментальный Mali850 patch

Был подготовлен экспериментальный Magisk ZIP с идеей изменения поведения Mali DVFS.

Он **не был подтверждён как рабочее решение**.

Поэтому он не является частью рекомендованной процедуры и не должен публиковаться как проверенный способ разблокировки 850 MHz.

## SELinux

Во время диагностики SELinux переводился в permissive для исследования доступности debugfs.

Это диагностический шаг, а не рекомендуемая постоянная конфигурация.

Если нужен безопасный daily-driver режим, проверяйте и возвращайте SELinux в штатное состояние.
