# Инструкция по загрузке списков

## Автоматическая загрузка

Для загрузки всех списков используйте скрипт `download_lists.sh`.

### Требования

- Linux, macOS или Windows (с WSL или Git Bash)
- Bash
- curl

### Запуск

```bash
cd "/home/tim/Списки SpiPrivacy"
bash download_lists.sh
```

### Скрипт делает следующее:

1. Скачивает каждый список в отдельную папку
2. Создает README.md с описанием и статистикой
3. Добавляет предупреждения для опасных списков
4. Подсчитывает общий размер и количество правил
5. Сообщает о неудачных загрузках

### Результат

```
================================
Успешно скачано: 41 из 45
Общий размер: 87484 KB (85 MB)
Всего правил: 3432291
================================
```

## Ручная загрузка

Если вы хотите скачать только определенные списки:

### Пример 1: Скачать один список

```bash
mkdir -p Sp/18
curl -L "https://easylist.to/easylist/easylist.txt" -o Sp/18/easylist.txt
```

### Пример 2: Скачать несколько списков

```bash
# EasyList
curl -L "https://easylist.to/easylist/easylist.txt" -o Sp/18/easylist.txt

# EasyPrivacy
curl -L "https://easylist.to/easylist/easyprivacy.txt" -o Sp/19/easyprivacy.txt

# Adguard Base
curl -L "https://raw.githubusercontent.com/AdguardTeam/FiltersRegistry/master/filters/filter_2_Base/filter.txt" -o Sp/14/adguard-base.txt
```

## Источники списков

### EasyList / EasyPrivacy
- https://easylist.to/
- https://easylist-downloads.adblockplus.org/

### AdGuard
- https://filters.adtidy.org/
- GitHub: AdguardTeam/FiltersRegistry

### uBlock Origin
- GitHub: uBlockOrigin/uAssets

### HaGezi
- https://github.com/hagezi/dns-blocklists

### Другие
- Phishing Army: https://phishing.army/
- Fanboy: https://secure.fanboy.co.nz/
- URLhaus: https://urlhaus.abuse.ch/

## Обновление списков

Списки обновляются их владельцами. Для получения последних версий:

1. Запустите скрипт загрузки
2. Или удалите папку списка и скачайте заново

## Проблемы с загрузкой

### Таймауты

Если скрипт сообщает о таймаутах:
```bash
❌ ОШИБКА: Не удалось скачать (код: 000)
```

**Решения:**
1. Попробуйте запустить скрипт позже
2. Проверьте интернет-соединение
3. Используйте VPN, если сайт заблокирован в вашем регионе

### Пустые файлы

Если скачанный файл слишком маленький (менее 100 байт):
- Сервер мог вернуть ошибку
- URL мог измениться
- Проверьте содержимое файла вручную

### Неверные кодировки

Если списки отображаются некорректно:
```bash
# Проверить кодировку
file Sp/18/easylist.txt

# Конвертировать в UTF-8 если нужно
iconv -f ISO-8859-1 -t UTF-8 Sp/18/easylist.txt > Sp/18/easylist-utf8.txt
```

## Добавление новых списков

Для добавления нового списка:

1. Отредактируйте `download_lists.sh`
2. Добавьте URL в массив `urls`
3. Добавьте имя файла в массив `filenames`
4. Добавьте описание в массив `descriptions`
5. Добавьте флаг предупреждения в массив `warn_flags` (опционально)
6. Запустите скрипт

### Пример добавления

```bash
# В массив urls
urls+=("https://example.com/blocklist.txt")

# В массив filenames
filenames+=("custom-blocklist.txt")

# В массив descriptions
descriptions+=("Мой кастомный список")

# В массив warn_flags (опционально)
warn_flags+=("")
```

## Список не скачался

Если список не скачался, в его папке будет создан README.md с пометкой об ошибке:

```markdown
## ⚠️ Статус: ОШИБКА ЗАГРУЗКИ

Этот список не удалось скачать. Возможные причины:
- Сервер недоступен
- Таймаут соединения
- URL изменился
```

### Не скачались (из текущего запуска):

- **#7 EasyList French** - `https://easylist-downloads.adblockplus.org/easylistfrench.txt`
- **#8 EasyList Germany** - `https://easylist-downloads.adblockplus.org/easylistgermany.txt`
- **#9 EasyList China** - `https://easylist-downloads.adblockplus.org/easylistchina.txt`
- **#16 Disconnect Tracking** - `https://s3.amazonaws.com/lists.disconnect.me/simple_tracking.txt`

### Альтернативные источники:

Для EasyList региональных списков попробуйте:
- https://easylist.to/
- https://filters.adtidy.org/extension/ublock/filters/

## Автоматизация

### Cron (Linux/macOS)

Добавьте в crontab для ежедневного обновления в 3:00 утра:

```bash
crontab -e
```

Добавьте строку:
```
0 3 * * * cd "/home/tim/Списки SpiPrivacy" && bash download_lists.sh >> logs/download.log 2>&1
```

### systemd Timer (Linux)

Создайте файл сервиса:
```ini
# /etc/systemd/system/spiprivacy-update.service
[Unit]
Description=Update SpiPrivacy Blocklists

[Service]
Type=oneshot
ExecStart=/bin/bash /home/tim/Списки\ SpiPrivacy/download_lists.sh
WorkingDirectory=/home/tim/Списки\ SpiPrivacy
```

И таймер:
```ini
# /etc/systemd/system/spiprivacy-update.timer
[Unit]
Description=Daily SpiPrivacy Blocklists Update

[Timer]
OnCalendar=daily
Persistent=true

[Install]
WantedBy=timers.target
```

Активируйте:
```bash
sudo systemctl enable spiprivacy-update.timer
sudo systemctl start spiprivacy-update.timer
```

---

**Для вопросов и проблем:** Создайте issue на GitHub проекта.
