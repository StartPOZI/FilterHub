# Download Guide

## Automatic Download

To download all lists, use the `download_lists.sh` script.

### Requirements

- Linux, macOS, or Windows (with WSL or Git Bash)
- Bash
- curl

### Run

```bash
cd "/home/tim/Списки SpiPrivacy"
bash download_lists.sh
```

### The script does:

1. Downloads each list to a separate folder
2. Creates README.md with description and statistics
3. Adds warnings for dangerous lists
4. Calculates total size and rule count
5. Reports failed downloads

### Result

```
================================
Downloaded: 41 of 45
Total size: 87484 KB (85 MB)
Total rules: 3432291
================================
```

## Manual Download

If you want to download specific lists only:

### Example 1: Download one list

```bash
mkdir -p Sp/18
curl -L "https://easylist.to/easylist/easylist.txt" -o Sp/18/easylist.txt
```

### Example 2: Download multiple lists

```bash
# EasyList
curl -L "https://easylist.to/easylist/easylist.txt" -o Sp/18/easylist.txt

# EasyPrivacy
curl -L "https://easylist.to/easylist/easyprivacy.txt" -o Sp/19/easyprivacy.txt

# Adguard Base
curl -L "https://raw.githubusercontent.com/AdguardTeam/FiltersRegistry/master/filters/filter_2_Base/filter.txt" -o Sp/14/adguard-base.txt
```

## List Sources

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

### Others
- Phishing Army: https://phishing.army/
- Fanboy: https://secure.fanboy.co.nz/
- URLhaus: https://urlhaus.abuse.ch/

## Updating Lists

Lists are updated by their owners. To get latest versions:

1. Run the download script
2. Or delete the list folder and re-download

## Download Problems

### Timeouts

If script reports timeouts:
```bash
❌ ERROR: Failed to download (code: 000)
```

**Solutions:**
1. Try running the script later
2. Check your internet connection
3. Use VPN if site is blocked in your region

### Empty Files

If downloaded file is too small (less than 100 bytes):
- Server might have returned an error
- URL might have changed
- Check file content manually

### Wrong Encodings

If lists display incorrectly:
```bash
# Check encoding
file Sp/18/easylist.txt

# Convert to UTF-8 if needed
iconv -f ISO-8859-1 -t UTF-8 Sp/18/easylist.txt > Sp/18/easylist-utf8.txt
```

## Adding New Lists

To add a new list:

1. Edit `download_lists.sh`
2. Add URL to `urls` array
3. Add filename to `filenames` array
4. Add description to `descriptions` array
5. Add warning flag to `warn_flags` array (optional)
6. Run the script

### Example:

```bash
# In urls array
urls+=("https://example.com/blocklist.txt")

# In filenames array
filenames+=("custom-blocklist.txt")

# In descriptions array
descriptions+=("My custom list")

# In warn_flags array (optional)
warn_flags+=("")
```

## List Not Downloaded

If a list failed to download, its folder will contain a README.md with error notice:

```markdown
## ⚠️ Status: DOWNLOAD ERROR

This list failed to download. Possible reasons:
- Server unavailable
- Connection timeout
- URL changed
```

### Alternative Sources:

For EasyList regional lists, try:
- https://easylist.to/
- https://filters.adtidy.org/extension/ublock/filters/

## Automation

### Cron (Linux/macOS)

Add to crontab for daily update at 3 AM:

```bash
crontab -e
```

Add line:
```
0 3 * * * cd "/home/tim/Списки SpiPrivacy" && bash download_lists.sh >> logs/download.log 2>&1
```

### systemd Timer (Linux)

Create service file:
```ini
# /etc/systemd/system/spiprivacy-update.service
[Unit]
Description=Update SpiPrivacy Blocklists

[Service]
Type=oneshot
ExecStart=/bin/bash /home/tim/Списки\ SpiPrivacy/download_lists.sh
WorkingDirectory=/home/tim/Списки\ SpiPrivacy
```

And timer:
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

Enable:
```bash
sudo systemctl enable spiprivacy-update.timer
sudo systemctl start spiprivacy-update.timer
```

---

**For questions and issues:** Create a GitHub issue for the project.
