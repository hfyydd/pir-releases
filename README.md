# pir

`pir-releases` 是 `pir` 的公开二进制发布仓库。这里提供可直接下载的安装包和使用说明，用来给外部用户安装和更新 `pir`。

源码仓库不在这里公开发布；这个仓库只负责 GitHub Releases 资产分发。

## 下载

到 Releases 页面下载最新版本：

- [Releases](https://github.com/hfyydd/pir-releases/releases)

当前提供的资产：

- macOS Apple Silicon: `pir-macos-arm64-vX.Y.Z.tar.gz`
- Windows x64: `pir-windows-x64-vX.Y.Z.zip`

## macOS 安装

下载对应版本后执行：

```bash
mkdir -p ~/.local/bin
tar -xzf pir-macos-arm64-v0.1.6.tar.gz
cp pir-macos-arm64-v0.1.6/pir ~/.local/bin/pir
chmod +x ~/.local/bin/pir
```

如果 `~/.local/bin` 还不在 `PATH` 里，把下面这行加到你的 shell 配置里：

```bash
export PATH="$HOME/.local/bin:$PATH"
```

然后启动：

```bash
pir
```

## Windows 安装

1. 下载 `pir-windows-x64-vX.Y.Z.zip`
2. 解压
3. 运行其中的 `pir.exe`

如果你想在 PowerShell 或 CMD 里直接调用，也可以把解压目录加入系统 `PATH`。

## 首次启动后会生成什么

首次启动 `pir` 时，会自动创建本地目录和配置：

- `~/.pir/pir.json`
- `~/.pir/workspace/`
- `~/.pi/agent/auth.json`
- `~/.pi/agent/sessions/`

其中：

- `~/.pir/pir.json` 是主配置文件
- `~/.pir/workspace` 是系统级 workspace
- `~/.pi/agent/sessions` 是默认会话历史目录

## 最常用的命令

打开交互界面：

```bash
pir
```

单次执行：

```bash
pir "帮我总结今天的工作重点"
```

查看运行状态：

```bash
pir status
pir doctor
pir context list
pir context detail
```

## 定时提醒

`pir` 内置了 cron / reminder 功能。

查看状态：

```bash
pir cron status
pir cron list
```

创建一次性提醒：

```bash
pir cron add --name "喝水提醒" --at "2026-04-03T15:00:00+08:00" --wake-main "到点喝水"
```

如果提醒是在 TUI 里创建的，到点后会回到当前主会话；如果任务来自外部 channel，就会回到对应 channel。

## Telegram / Feishu

`pir` 支持把 agent 接到 Telegram 或 Feishu。

常用命令：

```bash
pir channel status
pir channel config show
pir channel start
pir channel stop
```

Telegram 和 Feishu 的具体配置都写在：

```bash
~/.pir/pir.json
```

## 更新

更新方式很简单：

1. 从 Releases 下载新版本
2. 覆盖本地 `pir` 二进制
3. 重启 `pir`

## 卸载

只删程序：

```bash
rm -f ~/.local/bin/pir
```

连数据一起删：

```bash
rm -rf ~/.pir
rm -rf ~/.pi/agent
```

这会删除配置、workspace、认证信息和会话历史。

## 说明

- 这个仓库只存放公开可分发的二进制和 release 说明
- 不包含你的本地配置、workspace、auth 和会话数据
- 不公开 `pi-r` 源码仓库内容
