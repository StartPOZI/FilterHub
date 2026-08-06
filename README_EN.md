# SpiPrivacy Blocklists

Collection of adblocker lists for browsers with automatic download and organization.

![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)
![Lists](https://img.shields.io/badge/lists-44%20of%2045-brightgreen.svg)
![Size](https://img.shields.io/badge/size-115%20MB-yellow.svg)
![Rules](https://img.shields.io/badge/rules-3.9M-red.svg)

## 📊 Statistics

| Metric | Value |
|--------|-------|
| Total lists | 44 of 45 (all downloaded) |
| Total size | ~115 MB |
| Total rules | 3,900,000 |
| Last update | 2026-08-06 |

## 📁 Project Structure

```
SpiPrivacy/
├── Sp/              # Downloaded lists
│   ├── 1-45/       # Numbered folders
│   │   ├── README.md
│   │   └── *.txt    # Blocklist files
├── Doc/            # Documentation
├── LEVELS.md       # Protection levels (Russian)
├── LEVELS_EN.md    # Protection levels (English)
└── README.md       # This file
```

## 🔥 Top Lists

| List | Rules | Size | Description |
|------|-------|-------|-------------|
| HaGezi TIF (#39) | 2,175,386 | 43 MB | Threat Intelligence Feed |
| Adguard Spyware (#21) | 199,049 | 6.2 MB | Spyware protection |
| HaGezi Pro Plus (#45) | 241,964 | 5.2 MB | Professional list |
| Adguard Base (#14) | 166,793 | 7.6 MB | Base AdGuard filter |
| Phishing Army (#5) | 155,428 | 3.1 MB | Phishing protection |

## 📂 Categories

### 🔒 Privacy
- #19 EasyPrivacy
- #30 uBlock Privacy
- #24 Adguard TrackParam
- #16 Disconnect Tracking

### 🛡️ Security
- #5 Phishing Army
- #36 URLhaus Filter
- #33 uBlock Badware
- #17 NoCoin (crypto mining)

### 😤 Annoyances
- #23 Adguard Annoyances
- #37 Fanboy Annoyance
- #25 Adguard Cookies (cookie banners)
- #26 Adguard Popups

### 📺 Ad Blocking
- #18 EasyList - main list
- #14 Adguard Base
- #29 uBlock Filters

## 🚀 Quick Start

### Download lists

```bash
cd "/home/tim/Списки SpiPrivacy"
bash download_lists.sh
```

### Use in uBlock Origin

1. Open uBlock Origin settings
2. Go to "Filters" → "Filter lists"
3. Paste URL from `Sp/Number/README.md`
4. Click "Apply changes"

## 📖 Documentation

- [Full documentation](Doc/README.md)
- [Download guide](Doc/DOWNLOAD_GUIDE.md)
- [Protection levels](LEVELS_EN.md)

## 🔧 Scripts

- `download_lists.sh` - Download all lists
- `download_missing.sh` - Download missing via Tor

## 📄 License

This project is licensed under **Apache License 2.0**.

Individual lists have their own licenses - see their README.md files.

```
Copyright 2026 SpiPrivacy Project

Licensed under the Apache License, Version 2.0
```

## 🔗 Sources

- [EasyList](https://easylist.to/)
- [AdGuard](https://filters.adtidy.org/)
- [uBlock Origin](https://github.com/uBlockOrigin/uAssets)
- [HaGezi](https://github.com/hagezi/dns-blocklists)
- [Phishing Army](https://phishing.army/)
- [Fanboy](https://secure.fanboy.co.nz/)

---

**Made with ❤️ for privacy and security on the internet**
