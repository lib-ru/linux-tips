Команды для "правильной" записи **ISO** на **USB Flash Drive**.

1. Определить USB-накопитель при помощи команды `fdisk -l`.
2. Отмонтировать ВСЕ разделы с USB-накопителя командой `umount /dev/sdX*`, где `X` - буква накопителя (например, `umount /dev/sdc*`).
3. Загрузить ISO на USB-накопитель:

```bash
# Отмонтировать и очистить USB-накопитель.
umount /dev/sdX* && sgdisk -Z /dev/sdX

# Записать образ на USB-накопитель.
dd if=image.iso of=/dev/sdX bs=4M oflag=direct status=progress; sync

# Извлечь USB-накопитель.
eject /dev/sdX
```
