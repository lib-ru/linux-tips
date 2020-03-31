Заметки по работе с диском или дисковыми массивами.

#### Разметка и подключение диска

Чтобы создать на новом диске раздел, необходимо войти в программу `parted`:

```bash
parted -a optimal /dev/sdb
```

Выполнить следующие команды:

```bash
(parted) mklabel gpt
(parted) mkpart primary 0% 100%
(parted) quit
```

Создать файловую систему:

```bash
mkfs.xfs /dev/sdb1
```

Настроить автоматическое монтирование раздела в `/etc/fstab`:

```bash
/dev/sdb1 /home/storage xfs defaults 0 0
```
