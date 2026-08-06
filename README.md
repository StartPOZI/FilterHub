# SpiPrivacy Blocklists

Коллекция списков блокировщиков для браузеров и adblockers с автоматической загрузкой и структурированием.

![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)
![Lists](https://img.shields.io/badge/lists-45%20of%2045-brightgreen.svg)
![Size](https://img.shields.io/badge/size-86%20MB-yellow.svg)
![Rules](https://img.shields.io/badge/rules-3.4M-red.svg)

## 📋 Обзор

SpiPrivacy Blocklists - это проект, который автоматически скачивает и организует списки блокировщиков из различных проверенных источников, включая:

- **EasyList / EasyPrivacy** - Основные списки рекламы и приватности
- **AdGuard Filters** - Фильтры от команды AdGuard
- **uBlock Origin** - Фильтры от Raymond Hill
- **HaGezi** - Профессиональные DNS-списки
- **DuckDuckGo** - Tracker Radar списки
- И другие...

## 📊 Статистика

| Показатель | Значение |
|------------|----------|
| 📦 Всего списков | ✅ 45 из 45 (все скачано!) |
| 💾 Общий размер | ~86 MB |
| 📝 Всего правил | 3,457,877 |
| ⏳ Последнее обновление | 2026-08-06 |
| 🌐 Геоблокировка | Обход через Tor |

## 🚀 Быстрый старт

### Загрузка списков

```bash
cd "/home/tim/Списки SpiPrivacy"
bash download_lists.sh
```

### Использование в uBlock Origin

1. Откройте настройки uBlock Origin
2. Перейдите в "Фильтры" → "Списки фильтров"
3. Вставьте URL из папки `Sp/Номер/README.md`
4. Нажмите "Применить изменения"

## 📁 Структура проекта

```
SpiPrivacy/
├── Sp/                    # Скачанные списки
│   ├── 1/                # Номер списка
│   │   ├── README.md     # Описание
│   │   └── list.txt      # Сам список
│   └── ...
├── Doc/                  # Документация
│   ├── README.md        # Основная документация
│   ├── LICENSE.md       # Лицензия
│   └── DOWNLOAD_GUIDE.md # Инструкция по загрузке
├── sp.md                 # Обзор списков
├── download_lists.sh    # Скрипт загрузки
├── LICENSE              # Лицензия Apache 2.0
└── README.md           # Этот файл
```

## 🔥 Топ списков

| Список | Правил | Размер | Описание |
|--------|--------|--------|----------|
| HaGezi TIF | 2,175,386 | 43 MB | Threat Intelligence Feed |
| Adguard Spyware | 199,049 | 6.2 MB | Защита от шпионского ПО |
| HaGezi Pro Plus | 241,964 | 5.2 MB | Профессиональный список |
| Adguard Base | 166,793 | 7.6 MB | Базовый фильтр AdGuard |
| Phishing Army | 155,428 | 3.1 MB | Защита от фишинга |

Подробнее: [sp.md](sp.md)

## ⚠️ Предупреждения

### Google Ultra Strict (#1)
**Осторожно!** Может сломать:
- reCAPTCHA
- Google-шрифты
- Другие сервисы Google

### OISD Full (#10) / HaGezi Pro Plus (#45)
Большие списки, могут замедлить браузер.

## 📂 Категории

### 🔒 Приватность
- EasyPrivacy (#19)
- uBlock Privacy (#30)
- Adguard TrackParam (#24)
- Adguard Spyware (#21)

### 🛡️ Безопасность
- Phishing Army (#5)
- URLhaus Filter (#36)
- uBlock Badware (#33)
- NoCoin (#17) - защита от майнинга

### 😤 Аннойансы
- Adguard Annoyances (#23)
- Fanboy Annoyance (#37)
- Adguard Cookies (#25) - cookie-баннеры
- Adguard Popups (#26) - всплывающие окна

### 📺 Реклама
- EasyList (#18) - основной список
- Adguard Base (#14)
- uBlock Filters (#29)

## 📖 Документация

- [Полная документация](Doc/README.md)
- [Инструкция по загрузке](Doc/DOWNLOAD_GUIDE.md)
- [Лицензия](LICENSE)

## 🔧 Скрипт загрузки

Скрипт `download_lists.sh` автоматически:

1. Скачивает каждый список в отдельную папку
2. Создает README.md с описанием и статистикой
3. Добавляет предупреждения для опасных списков
4. Подсчитывает общий размер и количество правил

### Опции скрипта

Скрипт использует `curl` с таймаутом 60 секунд. Если сервер не отвечает, список пропускается с пометкой об ошибке.

## ✅ Успешно скачано через Tor

Следующие списки были скачаны через Tor прокси из-за геоблокировки:

- EasyList French (#7) - 89 правил
- EasyList Germany (#8) - 5,999 правил
- EasyList China (#9) - 19,461 правил
- Disconnect Tracking (#16) - 38 правил

Для повторной загрузки используйте:
```bash
bash download_missing.sh
```

## 🤝 Вклад

Вклад приветствуется! Для добавления новых списков:

1. Отредактируйте `download_lists.sh`
2. Добавьте URL, имя файла и описание
3. Запустите скрипт

## 📄 Лицензия

Этот проект распространяется под лицензией **Apache License 2.0**.

Отдельные списки имеют собственные лицензии - см. их README.md файлы.

```
Copyright 2026 SpiPrivacy Project

Licensed under the Apache License, Version 2.0
```

## 🔗 Источники

- [EasyList](https://easylist.to/)
- [AdGuard](https://filters.adtidy.org/)
- [uBlock Origin](https://github.com/uBlockOrigin/uAssets)
- [HaGezi](https://github.com/hagezi/dns-blocklists)
- [Phishing Army](https://phishing.army/)
- [Fanboy](https://secure.fanboy.co.nz/)

## 📞 Поддержка

Для вопросов и проблем:
- Проверьте [документацию](Doc/README.md)
- Посмотрите [инструкцию по загрузке](Doc/DOWNLOAD_GUIDE.md)

---

**Сделано с ❤️ для приватности и безопасности в интернете**
