<p align="center">
  <img src="assets/icon.png" width="128" height="128" alt="MyTwig 图标">
</p>

<h1 align="center">MyTwig</h1>

<p align="center">快速的原生 Git 客户端，支持 macOS、Windows 和 Linux</p>

<p align="center"><a href="README.md">English</a> | <b>简体中文</b></p>

MyTwig 是一款适用于 macOS、Windows 和 Linux 的桌面 Git 客户端。它以提交图的形式展示仓库的所有分支，用鼠标或键盘即可完成暂存、提交、建分支、合并、变基、贮藏和解决冲突。它是用 Go 编写的原生应用，不基于 Electron，也不需要我们的任何账号或服务器。

本仓库**只存放发布版本和签名的更新清单**，不包含源代码。

**[下载最新版本 →](https://github.com/HeroSizy/mytwig-releases/releases/latest)** · [全部版本](https://github.com/HeroSizy/mytwig-releases/releases)

**快速安装。** macOS 与 Linux（终端）：

```sh
curl -fsSL https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.sh | sh
```

Windows（PowerShell）：

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bor [Net.SecurityProtocolType]::Tls12; irm https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.ps1 | iex
```

这两条命令做了什么、如何更新和卸载、手动下载，以及 Homebrew、Scoop 和 winget，请见[下载与安装](#下载与安装)。

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="screenshots/main-dark.png">
  <img src="screenshots/main.png" alt="MyTwig 主窗口：仓库的提交图，包含分支、标签和合并，以及所选提交的详情" width="100%">
</picture>

| 差异视图 | 冲突编辑器 |
| --- | --- |
| ![提交的差异，带语法高亮，并标出行内改动](screenshots/diff.png) | ![冲突编辑器：双方版本并排，下方是可编辑的结果](screenshots/conflict.png) |

## 主要功能

- **提交图**：显示所有分支，带分支和标签标签、作者头像，列宽和列顺序都可调整。历史非常长的仓库也能流畅浏览。
- **暂存与提交**：可以按文件、按区块或按单行暂存或丢弃。提交框支持修订上一次提交（amend）、Signed-off-by、共同作者、提交模板，以及摘要长度提示。
- **拖放完成合并与变基**。合并前会预测冲突；交互式变基可以重排、压缩、改写和丢弃提交。
- **冲突编辑器**：上方并排显示双方版本，下方是可编辑的合并结果。
- **撤销与重做**大多数操作。**操作时间线**可以把仓库恢复到变基、重置、合并、拉取等操作之前的状态。
- **拆分提交**：把一个提交或尚未提交的改动按文件、区块或行拆成多个提交。**Absorb** 把暂存的修复并入它们所属的提交。
- **拉取请求与议题**：支持 GitHub（含 Enterprise）、GitLab、Gitea/Forgejo 和 Bitbucket Cloud。GitHub 的拉取请求可以直接在应用内审查。
- **菜单栏/托盘小组件**：显示等待你处理的拉取请求、CI 状态，以及最近使用的仓库的状态。
- **可选的 AI 辅助**，使用你自己的服务商：生成提交信息、解释提交或改动、撰写拉取请求描述、给出冲突解决建议、规划拆分提交。支持 Anthropic、兼容 OpenAI 接口的服务、Gemini、本机的 Ollama 或 LM Studio，以及 `claude`、`codex`、`copilot`、`gemini` 命令行工具。请求从你的电脑直接发往你选择的服务商。
- 此外还有：文件历史、追溯（blame）与行历史、bisect、reflog、提交图中的贮藏、工作树、子模块、Git LFS、Git Flow、补丁、提交签名（GPG、SSH、X.509）、SSH 密钥管理、多套身份配置、自定义命令、内置终端和命令面板。
- **英文和简体中文界面**，浅色/深色主题，强调色，以及 macOS 26 的 Liquid Glass 风格（仅 macOS）。

## 系统要求

| 平台 | 构建 | 说明 |
| --- | --- | --- |
| macOS | Apple 芯片（arm64）与 Intel（amd64），各有单独的版本 | macOS 12 Monterey 或更高版本 |
| Windows | x64（amd64）与 ARM64 | 64 位 Windows 10 或 11 |
| Linux | x64（amd64）与 ARM64 | 需要 GTK 3 和 WebKitGTK 4.1，`.deb` 会作为依赖自动安装 |

所有平台都需要安装 **Git 2.32 或更高版本**。MyTwig 使用你现有的 `git`，以及它的配置、凭据助手、钩子和 SSH 设置。部分功能需要更新的 Git：只贮藏已暂存改动需要 2.35，冲突预测和堆叠分支变基需要 2.38。如果找不到 Git 或版本过旧，窗口会提示如何安装或升级。

## 下载与安装

MyTwig 有三种安装方式，推荐使用一条命令安装。

1. [一条命令安装](#一条命令安装)：使用我们的安装脚本，适用于 macOS、Linux 和 Windows。
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

两条命令都会为当前用户安装最新版本，不需要管理员权限，装好后打开 MyTwig。在 macOS 上，脚本会选择适合你的 Mac 的版本（Apple 芯片或 Intel），先用 MyTwig 的公钥校验下载文件的 Ed25519 签名，再把 MyTwig 放进 `/Applications`（如果你无法写入 `/Applications`，则放进 `~/Applications`）。在 Linux 上脚本同样会校验签名，需要 OpenSSL 3.0 或更高版本（Debian 12、Ubuntu 22.04、Fedora 36、RHEL 9 及更新版本）。curl 不像浏览器那样给下载的文件加隔离标记（脚本本身也不会去改这个标记），所以 macOS **不会弹出 Gatekeeper 的“仍要打开”提示**。在 Windows 上，脚本会用该版本的 `SHA256SUMS` 校验安装程序的 SHA-256，然后静默运行安装程序；如果 Microsoft Defender SmartScreen 仍然提示“Windows 已保护你的电脑”，点按 **更多信息**，再点按 **仍要运行**（安装程序目前没有代码签名）。

**更新。** MyTwig 会自动更新（见[自动更新](#自动更新)）。你也可以随时再次运行同一条命令：它会用最新版本覆盖当前安装，设置保持不变。

**卸载。** 在 macOS 或 Linux 上运行：

```sh
curl -fsSL https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.sh | sh -s -- --uninstall
```

设置会保留。在 Windows 上请到 **设置 → 应用** 卸载 MyTwig。

### 包管理器

如果你习惯用包管理器管理应用，也可以用它们安装 MyTwig，并按下面各自的方法通过包管理器更新。

#### Homebrew（macOS）

```sh
brew install --cask herosizy/tap/mytwig
```

Homebrew 会像浏览器一样给下载的文件加上隔离标记，所以首次打开同样需要上面手动下载时的[“仍要打开”](#首次打开仍要打开)步骤；`brew upgrade` 会安装一份新的副本，之后可能需要再做一次。更新请运行 `brew upgrade --cask mytwig`。应用自带的更新在 Homebrew 安装中同样可用，但在你运行这条命令之前，Homebrew 显示的仍是它安装的版本。`brew uninstall --cask mytwig` 会删除应用并保留设置；加上 `--zap` 则同时删除设置、缓存和日志。

#### Scoop（Windows）

```powershell
scoop bucket add herosizy https://github.com/HeroSizy/scoop-bucket
scoop install herosizy/mytwig
```

Scoop 会把 MyTwig 安装到它自己的目录（`~\scoop\apps\mytwig`），并添加开始菜单快捷方式，不需要管理员权限。更新请运行 `scoop update mytwig`。应用自带的更新同样可用，但之后 Scoop 显示的仍是它安装的版本。`scoop uninstall mytwig` 会删除应用，设置保留在 `%APPDATA%\MyTwig`。

#### winget（Windows）——即将上线

```powershell
winget install HeroSizy.MyTwig
```

MyTwig 尚未进入 winget 软件源，上线后即可使用这条命令。它运行的是与手动下载相同的安装程序，只为当前用户安装。更新请运行 `winget upgrade HeroSizy.MyTwig`；应用自带的更新同样可用。

### 手动下载

也可以自己从[最新版本](https://github.com/HeroSizy/mytwig-releases/releases/latest)下载。下表是 0.2.0 的文件名；GitHub 会把文件名里的空格显示为点。

| 平台 | 文件 | 说明 |
| --- | --- | --- |
| macOS | `MyTwig 0.2.0 arm64.dmg` / `MyTwig 0.2.0 amd64.dmg` | 磁盘映像：`arm64` 适用于 Apple 芯片（M1 及更新），`amd64` 适用于 Intel Mac |
| Windows | `MyTwig Setup 0.2.0 amd64.exe` / `… arm64.exe` | 安装程序（为当前用户安装，无需管理员权限） |
| Linux | `mytwig_0.2.0_amd64.deb` / `…_arm64.deb` | Debian/Ubuntu 软件包 |
| macOS、Linux | `install.sh` | 一条命令安装所用的脚本；在 Linux 上也可以安装放在它旁边的 `mytwig-0.2.0-linux-<架构>.tar.gz` |
| Windows | `install.ps1` | 一条命令安装所用的脚本 |
| （全部） | `SHA256SUMS` | 安装程序、压缩包和脚本的 SHA-256 校验和；其中的文件名保留空格，而 GitHub 显示为点 |
| （全部） | `update-<平台>.json`、`mytwig-0.2.0-<平台>.tar.gz` | 供自动更新使用（Windows 的压缩包也供 Scoop 使用），无需手动下载 |

#### macOS

1. 下载适合你的 Mac 的磁盘映像：Apple 芯片（M1 及更新）用 `MyTwig 0.2.0 arm64.dmg`，Intel 用 `MyTwig 0.2.0 amd64.dmg`。不确定的话，打开苹果菜单 → **关于本机**：Apple 芯片显示 **芯片：Apple M…**，Intel 显示 **处理器：… Intel …**。
2. 打开它，把 **MyTwig** 拖进“应用程序”文件夹。
3. 从“应用程序”打开 MyTwig。首次打开需要多做一步，见下文。

##### 首次打开：“仍要打开”

此版本**没有使用 Apple 开发者 ID 签名，也未经 Apple 公证**，只有临时（ad-hoc）签名，所以首次打开时会被 Gatekeeper 拦截。这是正常现象。允许打开的方法如下：

**macOS 15 Sequoia 及更高版本**

1. 双击 MyTwig，系统提示无法验证该应用，点按 **完成**。
2. 打开 **系统设置 → 隐私与安全性**，向下滚动到 **安全性**。
3. 在关于“MyTwig”的提示旁点按 **仍要打开**，然后输入密码或使用触控 ID 确认。
4. 再次打开 MyTwig，点按 **打开**。

**macOS 12–14**

在“应用程序”中按住 Control 键点按（或右键点按）MyTwig，选择 **打开**，再在对话框中点按 **打开**。也可以按上面的方法，在 **隐私与安全性** 中点按 **仍要打开**。

这一步只需做一次。如果你信任下载来源，也可以在“终端”中运行：

```sh
xattr -dr com.apple.quarantine /Applications/MyTwig.app
```

#### Windows

1. 运行 `MyTwig Setup 0.2.0 amd64.exe`；ARM 设备请使用 `arm64` 安装程序。
2. 安装程序目前没有代码签名，**Microsoft Defender SmartScreen** 可能会弹出警告。点按 **更多信息**，再点按 **仍要运行**。
3. MyTwig 只为当前用户安装，位置是 `%LOCALAPPDATA%\Programs\MyTwig`。安装程序会添加开始菜单快捷方式，也可以选择添加桌面快捷方式。卸载请到 **设置 → 应用**。

#### Linux

**方式 A：安装脚本（推荐，可自动更新）。** 安装到当前用户的 `~/.local`，不需要 root 权限，并添加桌面菜单项；之后应用可以自行更新：

```sh
curl -fsSL https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.sh | sh
```

也可以把 `install.sh` 和对应架构的 `mytwig-0.2.0-linux-<架构>.tar.gz` 下载到同一目录，然后运行 `sh install.sh`。要卸载，运行 `sh install.sh --uninstall`，设置会保留。脚本不会安装 WebKitGTK；如果系统里没有，它会告诉你用哪条命令安装。

**方式 B：Debian/Ubuntu 软件包。**

```sh
sudo apt install ./mytwig_0.2.0_amd64.deb   # 或 _arm64.deb
```

软件包安装在 `/opt/mytwig`，**不会自动更新**。升级时请安装新版本的 `.deb`。

## 自动更新

MyTwig 会从本仓库检查新版本：启动时如果距上次检查已超过 30 分钟就检查一次，之后每 30 分钟检查一次。过程如下：

1. 从本仓库的**最新版本（latest release）**下载 `update-<平台>.json`。平台包括 `darwin-arm64`、`darwin-amd64`、`windows-amd64`、`windows-arm64`、`linux-amd64` 和 `linux-arm64`：每个版本只读取自己平台的清单，因此 Apple 芯片 Mac 会一直使用 arm64 版本。
2. 如果清单中的版本更新，MyTwig 会在窗口中显示该版本及其更新说明。你可以选择安装、跳过此版本或稍后提醒。
3. 安装时下载清单指向的压缩包（如果有从你当前版本出发的增量更新，则只下载更小的增量包），然后检查文件大小，并**用内置在应用中的公钥校验 Ed25519 签名**。没有用 MyTwig 密钥签名的更新会被拒绝。
4. 新版本先放在旧版本旁边再替换；替换失败会恢复旧版本。新版本在下次启动 MyTwig 时运行，或在你点按 **立即重新启动** 后运行。

更新通过 HTTPS 从 GitHub 下载，不需要账号或令牌，也不会发送关于你或你的仓库的任何信息。

可以在 **设置 → 通用 → 更新** 中修改这些行为：打开或关闭后台检查，选择发现更新后是否不经询问直接安装，或立即检查。在 macOS 上也可以使用 **MyTwig → 检查更新…**。设置的同一行还会显示当前版本和上次检查的时间。

有些安装方式无法自动更新，设置中会说明原因：开发版本、`.deb` 安装（位于 `/opt`，属于 root），以及当前用户无法写入的位置，例如 macOS 非管理员账户下 `/Applications` 中的应用。 通过 Homebrew、Scoop 或 winget 安装时，应用自带的更新同样可用，但包管理器显示的仍是它安装的版本，所以建议通过包管理器更新（见[包管理器](#包管理器)）。

## 隐私

MyTwig 没有使用情况统计，也没有自己的服务器。它只会连接你的 Git 远程仓库、你登录的代码托管平台（GitHub、GitLab、Gitea/Forgejo、Bitbucket）、头像服务、你配置的 AI 服务商（如有），以及用于检查更新的 GitHub。**设置 → 隐私** 中列出了它连接的所有主机。令牌保存在系统钥匙串中：macOS 的钥匙串、Windows 的凭据管理器，以及 Linux 的 Secret Service。

**崩溃报告是可选的，默认关闭。** 首次启动时 MyTwig 会询问一次，复选框默认不勾选；之后也可以在 **设置 → 隐私** 中更改。如果你打开它，每次崩溃的报告会通过 [Sentry](https://sentry.io) 发送给开发者。报告只包含：

- MyTwig、git 和操作系统的版本，以及平台（例如 `darwin-arm64`）；
- 崩溃发生在 MyTwig 代码中的位置：函数名、文件名和行号；
- 错误信息，其中的路径、URL、邮箱、引号内的文字和哈希都已去掉；
- 你最近运行的几个 MyTwig 命令的名称（例如“全部抓取”）；
- 一个随机的安装 ID，仅用于区分不同的安装。

报告绝不包含你的代码、文件路径、分支名、远程仓库、提交信息、姓名或邮箱。关闭时不会发送任何内容：崩溃只保存在你的电脑上，只有在你之后打开崩溃报告时才会发送。**设置 → 隐私 → 查看最近的报告…** 会原样显示发送（或已发送）的内容。

## 反馈

问题和反馈请提交到 [GitHub Issues](https://github.com/HeroSizy/mytwig-releases/issues)。

## 许可与条款

可免费使用，保留所有权利。

MyTwig 内置的第三方字体（Inter、IBM Plex Sans、JetBrains Mono、Fira Code、Cascadia Code、Caveat、马善政楷书 Ma Shan Zheng）均采用 SIL Open Font License 1.1。

Copyright © 2026 HeroSizy.
