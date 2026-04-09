# Codex Auth

[中文说明](./README.zh-CN.md)

This project is based on [Loongphy/codex-auth](https://github.com/Loongphy/codex-auth). This fork mainly keeps and extends the quota listing, refresh, and multi-account comparison improvements.

## Added Features and Fixes

- Added `list --refresh-all` to refresh all accounts before rendering the list
- Added `--view left|used|raw` to inspect quota by remaining, used, or raw values
- Added `SOURCE` to show whether quota data came from the API or local cache
- Added `REFRESHED` to show when a quota snapshot was last updated
- Clarified quota labels and fixed the old ambiguous `USAGE` semantics
- Improved multi-account readability to reduce confusion caused by stale cached rows

## Install by Platform

Release page:

```shell
https://github.com/ypp977/codex-auth/releases
```

Download the archive for your platform, extract it, and put `codex-auth` or `codex-auth.exe` on your system `PATH`.

### macOS

- Intel: `codex-auth-macOS-X64.tar.gz`
- Apple Silicon / M-series: `codex-auth-macOS-ARM64.tar.gz`

Example:

```shell
tar -xzf codex-auth-macOS-ARM64.tar.gz
chmod +x codex-auth
mv codex-auth /opt/homebrew/bin/codex-auth
```

For Intel Macs, you may also use:

```shell
/usr/local/bin
```

### Linux

Download:

- `codex-auth-Linux-X64.tar.gz`

Install:

```shell
tar -xzf codex-auth-Linux-X64.tar.gz
chmod +x codex-auth
sudo mv codex-auth /usr/local/bin/codex-auth
```

### Windows

Download:

- `codex-auth-Windows-X64.zip`
- `codex-auth-Windows-ARM64.zip`

Install:

1. Extract the zip archive
2. Move `codex-auth.exe` to a fixed directory such as `C:\Tools\codex-auth\`
3. Add that directory to your system `Path`

### Verify the Installation

```shell
codex-auth --version
codex-auth list
```

Current releases include 5 build targets:

- Linux x64
- macOS x64
- macOS arm64
- Windows x64
- Windows arm64

## Common Usage

List accounts and quota:

```shell
codex-auth list
codex-auth list --refresh-all
```

Switch quota views:

```shell
codex-auth list --view left
codex-auth list --view used
codex-auth list --view raw
```

Switch accounts and check status:

```shell
codex-auth switch
codex-auth status
```

Add or import accounts:

```shell
codex-auth login
codex-auth login --device-auth
codex-auth import /path/to/auth.json --alias personal
codex-auth import /path/to/auth-folder
codex-auth import --purge
```

Configure auto-switch:

```shell
codex-auth config auto enable
codex-auth config auto disable
codex-auth config auto --5h 20 --weekly 10
```

Configure API refresh:

```shell
codex-auth config api enable
codex-auth config api disable
```

Notes:

- `SOURCE` helps you tell whether quota data came from the API or local cache
- `REFRESHED` helps you judge whether a row may already be stale
- If you switch accounts for Codex CLI or Codex App, restart the client so the new account takes effect
