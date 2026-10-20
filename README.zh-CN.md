<p align="center">
  <img src="assets/icon.png" width="128" height="128" alt="MyTwig 图标">
</p>

<h1 align="center">MyTwig</h1>

<p align="center">快速的原生 Git 客户端，支持 macOS、Windows 和 Linux</p>

<p align="center"><a href="README.md">English</a> | <b>简体中文</b></p>

MyTwig 是一款适用于 macOS、Windows 和 Linux 的桌面 Git 客户端。它用提交图显示仓库的所有分支。你可以用鼠标或键盘暂存、提交、建分支、合并、变基、贮藏和解决冲突。MyTwig 是原生应用，我们用 Go 编写。它不使用 Electron，也不使用我们的任何账号或服务器。

本仓库**只包含发布版本和签名的更新清单**，不包含源代码。

**[下载最新版本 →](https://github.com/HeroSizy/mytwig-releases/releases/latest)** · [全部版本](https://github.com/HeroSizy/mytwig-releases/releases)

**快速安装。** macOS 与 Linux（终端）：

```sh
curl -fsSL https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.sh | sh
```

Windows（PowerShell）：

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bor [Net.SecurityProtocolType]::Tls12; irm https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.ps1 | iex
```

更多信息见[下载与安装](#下载与安装)。该部分说明这两条命令的作用，以及如何更新和卸载 MyTwig。它还说明如何手动下载，以及如何使用 Homebrew、Scoop 和 winget。

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="screenshots/main-dark.png">
  <img src="screenshots/main.png" alt="MyTwig 主窗口：仓库的提交图，包含分支、标签和合并，以及所选提交的详情" width="100%">
</picture>

| 差异视图 | 冲突编辑器 |
| --- | --- |
| ![提交的差异，带语法高亮，并标出行内改动](screenshots/diff.png) | ![冲突编辑器：双方版本并排，下方是可编辑的结果](screenshots/conflict.png) |

## 主要功能

- **提交图**：显示所有分支，带分支和标签标签以及作者头像。你可以调整列宽和列顺序。历史非常长的仓库也能流畅显示。
- **暂存与提交**：按文件、区块或单行暂存或丢弃。提交框支持修订上一次提交（amend）、Signed-off-by、共同作者、提交模板和摘要长度提示。
- **拖放完成分支、合并与变基**。合并前，MyTwig 会预测冲突。交互式变基可以重排、压缩、改写和丢弃提交。
- **冲突编辑器**：上方并排显示双方版本，下方是可编辑的结果。
- **撤销与重做**大多数操作。**操作时间线**可以把仓库恢复到变基、重置、合并、拉取等操作之前的状态。
- **拆分提交**：把一个提交或尚未提交的改动按文件、区块或行拆成多个提交。**Absorb** 把暂存的修复移入它们所属的提交。
- **拉取请求与议题**：支持 GitHub（含 Enterprise）、GitLab、Gitea/Forgejo 和 Bitbucket Cloud。你可以在应用内审查 GitHub 的拉取请求。
- **菜单栏/托盘小组件**：显示等待你处理的拉取请求、CI 状态，以及最近使用的仓库的状态。
- **可选的 AI 辅助**，使用你自己的服务商：提交信息、提交或改动的解释、拉取请求描述、冲突建议和拆分计划。MyTwig 支持 Anthropic、兼容 OpenAI 接口的服务、Gemini、本机的 Ollama 或 LM Studio，以及 `claude`、`codex`、`copilot`、`gemini` 命令行工具。请求从你的电脑直接发往你选择的服务商。
- 其他功能：文件历史、追溯（blame）与行历史、bisect、reflog、提交图中的贮藏、工作树、子模块、Git LFS、Git Flow 和补丁。MyTwig 还提供提交签名（GPG、SSH、X.509）、SSH 密钥管理、多套身份配置、自定义命令、内置终端和命令面板。
- **英文和简体中文界面**，浅色和深色主题，强调色，以及 macOS 26 的 Liquid Glass 风格（仅 macOS）。

## 系统要求

| 平台 | 构建 | 说明 |
| --- | --- | --- |
| macOS | Apple 芯片（arm64）与 Intel（amd64），各有单独的版本 | macOS 12 Monterey 或更高版本 |
| Windows | x64（amd64）与 ARM64 | 64 位 Windows 10 或 11 |
| Linux | x64（amd64）与 ARM64 | 需要 GTK 3 和 WebKitGTK 4.1。`.deb` 会把它们作为依赖安装。 |

所有平台都必须安装 **Git 2.32 或更高版本**。MyTwig 使用你现有的 `git`，以及它的配置、凭据助手、钩子和 SSH 配置。部分功能需要更新的 Git。只贮藏已暂存改动需要 Git 2.35。冲突预测和堆叠分支变基需要 Git 2.38。如果没有 Git 或 Git 版本过旧，窗口会告诉你如何安装或更新。

## 下载与安装

MyTwig 有三种安装方式。我们推荐一条命令安装。

1. [一条命令安装](#一条命令安装)：我们的安装脚本，适用于 macOS、Linux 和 Windows。
2. [包管理器](#包管理器)：Homebrew、Scoop，以及即将上线的 winget。
3. [手动下载](#手动下载)：从发布页面下载磁盘映像、安装程序或软件包。

### 一条命令安装

**macOS 与 Linux**（终端）：

```sh
curl -fsSL https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.sh | sh
```

**Windows**（PowerShell）：

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bor [Net.SecurityProtocolType]::Tls12; irm https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.ps1 | iex
```

两条命令都为当前用户安装最新版本，然后打开 MyTwig。它们不需要管理员权限。

**macOS。** 脚本选择适合你的 Mac 的版本（Apple 芯片或 Intel）。它用 MyTwig 的公钥校验下载文件的 Ed25519 签名。然后它把 MyTwig 放进 `/Applications`；如果你无法写入 `/Applications`，则放进 `~/Applications`。curl 不像浏览器那样给下载的文件加隔离标记，脚本也不修改这个标记。因此 macOS **不显示 Gatekeeper 的“仍要打开”提示**。

**Linux。** 脚本同样校验签名。为此，你必须有 OpenSSL 3.0 或更高版本（Debian 12、Ubuntu 22.04、Fedora 36、RHEL 9 及更新版本）。

**Windows。** 脚本用该版本的 `SHA256SUMS` 文件校验安装程序的 SHA-256。然后它静默运行安装程序。

> **注意：** 安装程序目前没有代码签名。如果 Microsoft Defender SmartScreen 显示“Windows 已保护你的电脑”，点按 **更多信息**。然后点按 **仍要运行**。

**更新。** MyTwig 会自行更新（见[自动更新](#自动更新)）。你也可以随时再次运行同一条命令。该命令用最新版本覆盖当前版本。你的设置不变。

**卸载。** 如果你使用 macOS 或 Linux，运行这条命令：

```sh
curl -fsSL https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.sh | sh -s -- --uninstall
```

该命令保留你的设置。如果你使用 Windows，在 **设置 → 应用** 中卸载 MyTwig。

### 包管理器

如果你用包管理器管理应用，也可以用它安装 MyTwig。请用同一个包管理器更新 MyTwig。下面列出每个包管理器的命令。

#### Homebrew（macOS）

```sh
brew install --cask herosizy/tap/mytwig
```

> **注意：** Homebrew 会像浏览器一样给下载的文件加隔离标记。因此首次打开时，需要执行与手动下载相同的[“仍要打开”](#首次打开仍要打开)步骤。`brew upgrade` 会安装一份新的副本，所以升级后可能需要再执行一次这些步骤。

- 要更新 MyTwig，运行 `brew upgrade --cask mytwig`。
- 应用自带的更新在 Homebrew 安装中同样可用。但在你运行上面的命令之前，Homebrew 显示的仍是它安装的版本。
- 要删除应用并保留设置，运行 `brew uninstall --cask mytwig`。
- 要同时删除设置、缓存和日志，在命令中加上 `--zap`。

#### Scoop（Windows）

```powershell
scoop bucket add herosizy https://github.com/HeroSizy/scoop-bucket
scoop install herosizy/mytwig
```

Scoop 把 MyTwig 安装到它自己的目录（`~\scoop\apps\mytwig`），并添加开始菜单快捷方式。它不需要管理员权限。

- 要更新 MyTwig，运行 `scoop update mytwig`。
- 应用自带的更新同样可用。但之后 Scoop 显示的仍是它安装的版本。
- 要删除 MyTwig，运行 `scoop uninstall mytwig`。你的设置保留在 `%APPDATA%\MyTwig`。

#### winget（Windows）——即将上线

```powershell
winget install HeroSizy.MyTwig
```

> **注意：** MyTwig 尚未进入 winget 软件源。进入软件源后，这条命令即可使用。

该命令运行与手动下载相同的安装程序，只为当前用户安装。要更新 MyTwig，运行 `winget upgrade HeroSizy.MyTwig`。应用自带的更新同样可用。

### 手动下载

你也可以从[最新版本](https://github.com/HeroSizy/mytwig-releases/releases/latest)下载文件。下表是 0.2.0 版本的文件名。GitHub 把文件名中的空格显示为点。

| 平台 | 文件 | 说明 |
| --- | --- | --- |
| macOS | `MyTwig 0.2.0 arm64.dmg` / `MyTwig 0.2.0 amd64.dmg` | 磁盘映像：`arm64` 适用于 Apple 芯片（M1 及更新），`amd64` 适用于 Intel Mac |
| Windows | `MyTwig Setup 0.2.0 amd64.exe` / `… arm64.exe` | 安装程序（只为当前用户安装，不需要管理员权限） |
| Linux | `mytwig_0.2.0_amd64.deb` / `…_arm64.deb` | Debian/Ubuntu 软件包 |
| macOS、Linux | `install.sh` | 一条命令安装所用的脚本。在 Linux 上，它也可以安装同一目录中的 `mytwig-0.2.0-linux-<架构>.tar.gz` 文件 |
| Windows | `install.ps1` | 一条命令安装所用的脚本 |
| （全部） | `SHA256SUMS` | 安装程序、压缩包和脚本的 SHA-256 校验和。文件中的文件名保留空格，而 GitHub 显示为点 |
| （全部） | `update-<平台>.json`、`mytwig-0.2.0-<平台>.tar.gz` | 自动更新使用这些文件。Scoop 也使用 Windows 压缩包。你不必下载这些文件。 |

#### macOS

1. 下载适合你的 Mac 的磁盘映像：
   - Apple 芯片（M1 及更新）：`MyTwig 0.2.0 arm64.dmg`
   - Intel：`MyTwig 0.2.0 amd64.dmg`
2. 打开磁盘映像。
3. 把 **MyTwig** 拖进 **应用程序**。
4. 从 **应用程序** 打开 MyTwig。

> **注意：** 如果你不确定 Mac 的芯片，选择苹果菜单 → **关于本机**。Apple 芯片显示 **芯片：Apple M…**。Intel 显示 **处理器：… Intel …**。

> **注意：** 首次打开需要再执行一组步骤。见下文。

##### 首次打开：“仍要打开”

此版本**没有 Apple 开发者 ID 签名，Apple 也没有对它进行公证**。它只有临时（ad-hoc）签名。因此首次打开时，Gatekeeper 会拦截 MyTwig。这是正常现象。要允许 MyTwig 打开，请执行与你的 macOS 版本对应的步骤。

**macOS 15 Sequoia 及更高版本**

1. 双击 MyTwig。
2. 当对话框提示 Apple 无法验证 MyTwig 时，点按 **完成**。
3. 打开 **系统设置 → 隐私与安全性**。
4. 滚动到 **安全性**。
5. 在关于“MyTwig”的提示旁，点按 **仍要打开**。
6. 输入密码或使用触控 ID 确认。
7. 再次打开 MyTwig。
8. 点按 **打开**。

**macOS 12–14**

1. 在 **应用程序** 中，按住 Control 键点按（或右键点按）MyTwig。
2. 选择 **打开**。
3. 在对话框中，点按 **打开**。

你也可以按上面的步骤，使用 **系统设置 → 隐私与安全性 → 仍要打开**。

这些步骤只需执行一次。如果你信任下载来源，也可以在“终端”中运行这条命令：

```sh
xattr -dr com.apple.quarantine /Applications/MyTwig.app
```

> **警告：** 只有在你信任下载来源时，才运行这条命令。该命令会删除 MyTwig 的隔离标记。

#### Windows

1. 运行适合你的设备的安装程序：
   - x64：`MyTwig Setup 0.2.0 amd64.exe`
   - ARM：`MyTwig Setup 0.2.0 arm64.exe`
2. 如果 **Microsoft Defender SmartScreen** 显示警告，点按 **更多信息**。
3. 点按 **仍要运行**。

> **注意：** 安装程序目前没有代码签名。因此 SmartScreen 可能显示警告。

MyTwig 只为当前用户安装，位置是 `%LOCALAPPDATA%\Programs\MyTwig`。安装程序会添加开始菜单快捷方式。如果你选择该选项，它还会添加桌面快捷方式。要卸载 MyTwig，请使用 **设置 → 应用**。

#### Linux

**方式 A：安装脚本（推荐，可自行更新）。** 脚本把 MyTwig 安装到当前用户的 `~/.local`。它不需要 root 权限。它会添加桌面菜单项。安装后，应用可以自行更新：

```sh
curl -fsSL https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.sh | sh
```

你也可以从本地文件安装 MyTwig：

1. 把 `install.sh` 下载到一个目录。
2. 把对应架构的 `mytwig-0.2.0-linux-<架构>.tar.gz` 文件下载到同一目录。
3. 在该目录中运行 `sh install.sh`。

要删除 MyTwig，运行 `sh install.sh --uninstall`。该命令保留你的设置。

> **注意：** 脚本不安装 WebKitGTK。如果你的电脑没有 WebKitGTK，脚本会显示安装它的命令。

**方式 B：Debian/Ubuntu 软件包。**

```sh
sudo apt install ./mytwig_0.2.0_amd64.deb   # 或 _arm64.deb
```

软件包把 MyTwig 安装到 `/opt/mytwig`。

> **注意：** 软件包**不会自行更新**。要更新 MyTwig，请安装新版本的 `.deb`。

## 自动更新

MyTwig 从本仓库获取新版本。启动时，如果距上次检查已超过 30 分钟，它就检查一次。之后它每 30 分钟检查一次。更新过程如下：

1. MyTwig 从本仓库的**最新版本（latest release）**下载 `update-<平台>.json`。平台包括 `darwin-arm64`、`darwin-amd64`、`windows-amd64`、`windows-arm64`、`linux-amd64` 和 `linux-arm64`。每个版本只读取自己的文件。因此 Apple 芯片 Mac 始终使用 arm64 版本。
2. 如果清单中有更新的版本，MyTwig 会在窗口中显示该版本及其更新说明。你可以安装它、跳过此版本，或稍后接收提醒。
3. 如果你安装更新，MyTwig 下载清单中的压缩包。如果有从你当前版本出发的更小的增量包，MyTwig 下载增量包。然后 MyTwig 检查压缩包的大小。它还**用应用内置的公钥校验 Ed25519 签名**。MyTwig 拒绝没有 MyTwig 密钥签名的更新。
4. MyTwig 把新版本放在旧版本旁边。如果失败，MyTwig 恢复旧版本。MyTwig 在下次启动时，或在你点按 **立即重新启动** 后，使用新版本。

MyTwig 通过 HTTPS 从 GitHub 下载更新。你不需要账号或令牌。MyTwig 不发送关于你或你的仓库的任何数据。

要修改这些设置，请前往 **设置 → 通用 → 更新**。你可以在这里：

- 打开或关闭后台检查。
- 选择 MyTwig 是否不经询问直接安装更新。
- 立即检查。

在 macOS 上，你也可以使用 **MyTwig → 检查更新…**。设置的同一行还显示当前版本和上次检查的时间。

有些安装方式无法自行更新，设置中会说明。这些安装方式是：

- 开发版本。
- `.deb` 安装，因为它位于 `/opt`，属于 root。
- 你无法写入的副本。例如 macOS 非管理员账户下 `/Applications` 中的应用。

通过 Homebrew、Scoop 或 winget 安装时，应用也可以自行更新。但之后包管理器显示的仍是它安装的版本。因此请用包管理器更新这些安装（见[包管理器](#包管理器)）。

## 隐私

MyTwig 没有使用情况统计，也没有自己的服务器。它连接你的 Git 远程仓库，以及你有账号的代码托管平台（GitHub、GitLab、Gitea/Forgejo、Bitbucket）。它还连接头像服务、你的 AI 服务商（如有），以及用于更新的 GitHub。**设置 → 隐私** 列出 MyTwig 连接的所有主机。MyTwig 把令牌保存在系统钥匙串中：macOS 的钥匙串、Windows 的凭据管理器，以及 Linux 的 Secret Service。

**崩溃报告是可选的，默认关闭。** 首次启动时，MyTwig 会询问一次，复选框默认不勾选。你之后可以在 **设置 → 隐私** 中更改。如果你允许崩溃报告，MyTwig 会通过 [Sentry](https://sentry.io) 把每次崩溃的报告发送给开发者。报告只包含以下数据：

- MyTwig、git 和操作系统的版本，以及平台（例如 `darwin-arm64`）；
- 崩溃在 MyTwig 代码中的位置：函数名、文件名和行号；
- 错误信息，不含路径、URL、邮箱、引号内的文字和哈希；
- 你最近运行的几个 MyTwig 命令的名称（例如“全部抓取”）；
- 一个随机的安装 ID。MyTwig 只用它区分不同的安装。

报告绝不包含你的代码、文件路径、分支名、远程仓库、提交信息、姓名或邮箱。如果崩溃报告关闭，MyTwig 不发送任何内容。它只把崩溃报告保存在你的电脑上。如果你之后允许崩溃报告，MyTwig 才发送该报告。**设置 → 隐私 → 查看最近的报告…** 会原样显示 MyTwig 发送（或已发送）的内容。

## 反馈

请在 [GitHub Issues](https://github.com/HeroSizy/mytwig-releases/issues) 中报告问题和提交反馈。

## 许可与条款

你可以免费使用 MyTwig。保留所有权利。

MyTwig 内置第三方字体（Inter、IBM Plex Sans、JetBrains Mono、Fira Code、Cascadia Code、Caveat、马善政楷书 Ma Shan Zheng）。每种字体都采用 SIL Open Font License 1.1。

Copyright © 2026 HeroSizy.
