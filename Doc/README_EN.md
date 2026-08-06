# SpiPrivacy Blocklists - Documentation

## Table of Contents

1. [Overview](#overview)
2. [Project Structure](#project-structure)
3. [Using Lists](#using-lists)
4. [List Categories](#list-categories)
5. [FAQ](#faq)

## Overview

SpiPrivacy Blocklists is a collection of 44 adblocker lists for browsers and adblock extensions. The project automatically downloads and organizes lists from various trusted sources.

### Project Statistics

| Metric | Value |
|------------|----------|
| Total lists | 44 downloaded / 45 total |
| Total size | ~115 MB |
| Total rules | 3,900,000 |
| Last update | 2026-08-06 |

## Project Structure

```
SpiPrivacy/
├── Sp/              # Downloaded lists
│   ├── 1/          # List number
│   │   ├── README.md # Description
│   │   └── list.txt # The list itself
│   └── ...
├── Doc/            # Documentation
│   ├── README.md   # This file
│   ├── LICENSE.md  # License
│   └── DOWNLOAD_GUIDE.md # Download guide
├── LEVELS_EN.md    # Protection levels
├── README_EN.md    # Main documentation
├── download_lists.sh # Download script
└── LICENSE         # Apache 2.0 License
```

## Using Lists

### In uBlock Origin

1. Open uBlock Origin settings
2. Go to "Filters" → "Filter lists"
3. In "Custom" section, paste URL from list's README.md
4. Click "Apply changes"

### In AdGuard

1. Open AdGuard → Settings → Ad blocking
2. Click "Add list"
3. Paste the URL and click OK

### In Brave Browser

1. Go to `brave://settings/adblocking`
2. Expand "Custom lists"
3. Add the URL

## List Categories

### 🔒 Privacy

Lists for tracking and data collection protection:

- **#19 EasyPrivacy** - Main privacy list
- **#30 uBlock Privacy** - uBlock filters
- **#24 Adguard TrackParam** - Tracking parameters
- **#21 Adguard Spyware** - Spyware protection

### 🛡️ Security

Malware and phishing protection:

- **#5 Phishing Army** - Phishing sites (155K rules)
- **#36 URLhaus Filter** - Malicious URLs
- **#33 uBlock Badware** - Badware protection
- **#17 NoCoin** - Crypto mining protection

### 😤 Annoyances

Annoying elements blocking:

- **#23 Adguard Annoyances** - From AdGuard (68K rules)
- **#37 Fanboy Annoyance** - From Fanboy (55K rules)
- **#25 Adguard Cookies** - Cookie banners
- **#26 Adguard Popups** - Popups

### 📺 Ad Blocking

Main ad blocking lists:

- **#18 EasyList** - Main list (86K rules)
- **#14 Adguard Base** - Base filter (166K rules)
- **#29 uBlock Filters** - uBlock filters

### 🔥 Professional

Maximum protection:

- **#39 HaGezi TIF** - 2.1M rules, 43 MB
- **#45 HaGezi Pro Plus** - 241K rules, 5.2 MB

### 🌍 Regional

- **#20 Adguard Russian** - Russian sites
- **#7 EasyList French** - French
- **#8 EasyList Germany** - German
- **#9 EasyList China** - Chinese
- **#13 DDG US Tracking** - US (471K rules)

## FAQ

### How much space do lists take?

All lists together take about **115 MB**. The largest is HaGezi TIF (43 MB).

### Can I use all lists simultaneously?

Not recommended. Use:
1. One main ad list (EasyList or Adguard Base)
2. One privacy list (EasyPrivacy)
3. Additional lists as needed

### What does "not downloaded" mean?

The server didn't respond within 60 seconds. Try later or use alternative sources.

### How to update lists?

Run the download script:
```bash
cd "/home/tim/Списки SpiPrivacy"
bash download_lists.sh
```

### Which is the most powerful list?

HaGezi TIF (#39) with 2,175,386 rules. It's also the largest (43 MB).

## Sources

Lists are downloaded from various trusted sources:
- EasyList / EasyPrivacy
- AdGuard Team
- uBlock Origin
- HaGezi
- Fanboy
- Phishing Army
- DuckDuckGo Tracker Radar
- And others

## License

Project is distributed under Apache License 2.0. See [LICENSE.md](LICENSE.md).

Individual lists have their own licenses - see their README.md files.

---

**Created:** 2026-08-06
