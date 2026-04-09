# Codex Auth

[English](./README.md)

本项目基于 [Loongphy/codex-auth](https://github.com/Loongphy/codex-auth) 开发，当前 fork 主要保留并增强了额度展示、刷新和多账号对比相关能力。

## 新增功能与修复

- 新增 `list --refresh-all`，支持在列表输出前刷新所有账号额度
- 新增 `--view left|used|raw`，支持按剩余、已用和原始值查看额度
- 新增 `SOURCE` 字段，用于区分额度数据来自 API 还是本地缓存
- 新增 `REFRESHED` 字段，用于显示额度快照最近一次刷新时间
- 调整额度展示语义，修复原先 `USAGE` 表意不清的问题
- 改善多账号列表对比时的可读性，减少非活跃账号缓存数据带来的误判

## 各系统安装方法

发布地址：

```shell
https://github.com/ypp977/codex-auth/releases
```

下载对应系统的压缩包，解压后把 `codex-auth` 或 `codex-auth.exe` 放到系统 `PATH` 中即可。

### macOS

- Intel：`codex-auth-macOS-X64.tar.gz`
- Apple Silicon / M 系列：`codex-auth-macOS-ARM64.tar.gz`

示例：

```shell
tar -xzf codex-auth-macOS-ARM64.tar.gz
chmod +x codex-auth
mv codex-auth /opt/homebrew/bin/codex-auth
```

如果你是 Intel Mac，也可以放到：

```shell
/usr/local/bin
```

### Linux

下载：

- `codex-auth-Linux-X64.tar.gz`

安装：

```shell
tar -xzf codex-auth-Linux-X64.tar.gz
chmod +x codex-auth
sudo mv codex-auth /usr/local/bin/codex-auth
```

### Windows

下载：

- `codex-auth-Windows-X64.zip`
- `codex-auth-Windows-ARM64.zip`

安装：

1. 解压 zip 压缩包
2. 把 `codex-auth.exe` 放到固定目录，例如 `C:\Tools\codex-auth\`
3. 把该目录加入系统 `Path`

### 安装验证

```shell
codex-auth --version
codex-auth list
```

当前 release 包含 5 个构建目标：

- Linux x64
- macOS x64
- macOS arm64
- Windows x64
- Windows arm64

## 常用操作

查看账号和额度：

```shell
codex-auth list
codex-auth list --refresh-all
```

切换额度视图：

```shell
codex-auth list --view left
codex-auth list --view used
codex-auth list --view raw
```

切换账号与查看状态：

```shell
codex-auth switch
codex-auth status
```

添加或导入账号：

```shell
codex-auth login
codex-auth login --device-auth
codex-auth import /path/to/auth.json --alias personal
codex-auth import /path/to/auth-folder
codex-auth import --purge
```

自动切号配置：

```shell
codex-auth config auto enable
codex-auth config auto disable
codex-auth config auto --5h 20 --weekly 10
```

API 刷新配置：

```shell
codex-auth config api enable
codex-auth config api disable
```

说明：

- `SOURCE` 可以帮助判断额度数据来自 API 还是本地缓存
- `REFRESHED` 可以帮助判断当前这一行数据是否已经过期
- 如果你在 Codex CLI 或 Codex App 中切换了账号，通常需要重启客户端后配置才会生效
