<p align="center">
  <img src="assets/icon.png" width="128" height="128" alt="MyTwig icon">
</p>

<h1 align="center">MyTwig</h1>

<p align="center">A fast, native Git client for macOS, Windows and Linux</p>

<p align="center">Built with <a href="https://github.com/egoist/mygo">MyGo</a>.</p>

<p align="center"><b>English</b> | <a href="README.zh-CN.md">简体中文</a></p>

MyTwig is a desktop Git client for macOS, Windows and Linux. It shows all the branches of a repository in a commit graph. You can stage, commit, branch, merge, rebase, stash and resolve conflicts with the mouse or the keyboard. MyTwig is a native app, and we wrote it in Go. It does not use Electron. It does not use an account or a server of ours.

This repository contains **release builds and signed update manifests only**. It does not contain source code.

**[Download the latest release →](https://github.com/HeroSizy/mytwig-releases/releases/latest)** · [All releases](https://github.com/HeroSizy/mytwig-releases/releases)

**Quick install.** macOS and Linux (Terminal):

```sh
curl -fsSL https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.sh | sh
```

Windows (PowerShell):

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bor [Net.SecurityProtocolType]::Tls12; irm https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.ps1 | iex
```

For more information, see [Download and install](#download-and-install). That section tells you what these commands do. It also tells you how to update and uninstall MyTwig. It also shows the manual downloads, and how to use Homebrew, Scoop and winget.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="screenshots/main-dark.png">
  <img src="screenshots/main.png" alt="MyTwig's main window: the commit graph of a repository with branches, tags and merges, and the details of the selected commit" width="100%">
</picture>

| Diff view | Conflict editor |
| --- | --- |
| ![A commit's diff, syntax-highlighted, with changes highlighted within lines](screenshots/diff.png) | ![The conflict editor: ours and theirs side by side above the editable result](screenshots/conflict.png) |

## Features

- **Commit graph** of all branches, with branch and tag labels and author avatars. You can change the width and the order of the columns. The graph stays fast on very large histories.
- **Stage and commit**: stage or discard full files, hunks or single lines. The commit box has amend, sign-off, co-authors, commit templates and hints for the summary length.
- **Branches, merges and rebases** with drag and drop. MyTwig predicts conflicts before you merge. With an interactive rebase, you can reorder, squash, reword and drop commits.
- **Conflict editor**. It shows ours and theirs side by side above an editable result.
- **Undo and redo** for most operations. The **Operation Timeline** can restore the repository to its state before a rebase, reset, merge, pull and other operations.
- **Split a commit**, or your uncommitted changes, into many commits by file, hunk or line. **Absorb** moves staged fixes into the commits that they belong to.
- **Pull requests and issues** from GitHub (also Enterprise), GitLab, Gitea/Forgejo and Bitbucket Cloud. You can review GitHub pull requests in the app.
- **Menu bar / tray companion**. It shows the pull requests that wait for you, the CI status and the status of your recent repositories.
- **Optional AI help** with your own provider: commit messages, explanations of a commit or a change, pull request descriptions, conflict suggestions and split plans. MyTwig supports Anthropic, OpenAI-compatible APIs, Gemini, local Ollama or LM Studio, and the `claude`, `codex`, `copilot` and `gemini` CLIs. Requests go directly from your computer to the provider that you select.
- More features: file history, blame and line history, bisect, reflog, stashes in the graph, worktrees, submodules, Git LFS, Git Flow and patches. MyTwig also has commit signatures (GPG, SSH, X.509), SSH key management, profiles, custom commands, a built-in terminal and a command palette.
- **English and Simplified Chinese**, light and dark themes, accent colors, and the macOS 26 Liquid Glass style (on macOS).

## System requirements

| Platform | Builds | Notes |
| --- | --- | --- |
| macOS | Apple silicon (arm64) and Intel (amd64), a build for each | macOS 12 Monterey or later |
| Windows | x64 (amd64) and ARM64 | 64-bit Windows 10 or 11 |
| Linux | x64 (amd64) and ARM64 | Needs GTK 3 and WebKitGTK 4.1. The `.deb` installs them as dependencies. |

On all platforms, you must install **Git 2.32 or later**. MyTwig uses the `git` that you have, with its configuration, credential helpers, hooks and SSH configuration. Some features need a newer Git. The staged-only stash needs Git 2.35. Conflict prediction and stacked rebases need Git 2.38. If you do not have Git, or if your Git is too old, the window tells you how to install or update it.

## Download and install

You can install MyTwig in three ways. We recommend the one-command install.

1. [Install with one command](#install-with-one-command): our install scripts for macOS, Linux and Windows.
2. [Package managers](#package-managers): Homebrew, Scoop and, soon, winget.
3. [Download manually](#download-manually): the disk image, the installer or the package from the release page.

### Install with one command

**macOS and Linux** (Terminal):

```sh
curl -fsSL https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.sh | sh
```

**Windows** (PowerShell):

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bor [Net.SecurityProtocolType]::Tls12; irm https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.ps1 | iex
```

The two commands install the latest version for your user, and then open MyTwig. They do not need administrator rights.

**macOS.** The script selects the build for your Mac (Apple silicon or Intel). It examines the Ed25519 signature of the download with the MyTwig key. Then it puts MyTwig in `/Applications`, or in `~/Applications` if you cannot write to `/Applications`. Unlike a browser, curl does not put a quarantine flag on the download, and the script does not change the flag. Thus, macOS shows **no Gatekeeper "Open Anyway" prompt**.

**Linux.** The script also examines the signature. For this, you must have OpenSSL 3.0 or later (Debian 12, Ubuntu 22.04, Fedora 36, RHEL 9 and later).

**Windows.** The script compares the SHA-256 of the installer with the `SHA256SUMS` file of the release. Then it runs the installer silently.

> **NOTE:** The installer does not have a code signature yet. If Microsoft Defender SmartScreen shows "Windows protected your PC", click **More info**. Then click **Run anyway**.

**Update.** MyTwig updates itself (see [Updates](#updates)). You can also run the same command again at any time. The command installs the latest version over your current version. Your settings do not change.

**Uninstall.** If you use macOS or Linux, run this command:

```sh
curl -fsSL https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.sh | sh -s -- --uninstall
```

The command keeps your settings. If you use Windows, uninstall MyTwig in **Settings → Apps**.

### Package managers

If you use a package manager for your apps, you can also install MyTwig with it. Use the same package manager to update MyTwig. The sections below show the commands for each package manager.

#### Homebrew (macOS)

```sh
brew install --cask herosizy/tap/mytwig
```

> **NOTE:** Homebrew puts a quarantine flag on the download, as a browser does. Thus, the first launch needs the same ["Open Anyway"](#first-launch-open-anyway) procedure as a manual download. `brew upgrade` installs a new copy, so you possibly must do the procedure again after an upgrade.

- To update MyTwig, run `brew upgrade --cask mytwig`.
- The updater of the app also works in a Homebrew install. But Homebrew shows the version that it installed until you run the command above.
- To remove the app and keep your settings, run `brew uninstall --cask mytwig`.
- To also remove the settings, caches and logs, add `--zap` to the command.

#### Scoop (Windows)

```powershell
scoop bucket add herosizy https://github.com/HeroSizy/scoop-bucket
scoop install herosizy/mytwig
```

Scoop installs MyTwig in its own folder (`~\scoop\apps\mytwig`) and adds a Start menu shortcut. It does not need administrator rights.

- To update MyTwig, run `scoop update mytwig`.
- The updater of the app also works. But Scoop continues to show the version that it installed.
- To remove MyTwig, run `scoop uninstall mytwig`. Your settings stay in `%APPDATA%\MyTwig`.

#### winget (Windows) — available soon

```powershell
winget install HeroSizy.MyTwig
```

> **NOTE:** MyTwig is not in the winget repository yet. This command will work when MyTwig is in the repository.

The command runs the same installer as the manual download, for your user only. To update MyTwig, run `winget upgrade HeroSizy.MyTwig`. The updater of the app also works.

### Download manually

You can also download the files from the [latest release](https://github.com/HeroSizy/mytwig-releases/releases/latest). In the names below, `<version>` is the version number of the release. GitHub shows spaces in asset names as dots.

| Platform | File | What it is |
| --- | --- | --- |
| macOS | `MyTwig <version> arm64.dmg` / `MyTwig <version> amd64.dmg` | Disk image: `arm64` for Apple silicon (M1 and later), `amd64` for Intel Macs |
| Windows | `MyTwig Setup <version> amd64.exe` / `… arm64.exe` | Installer (for your user only, no administrator rights necessary) |
| Linux | `mytwig_<version>_amd64.deb` / `…_arm64.deb` | Debian/Ubuntu package |
| macOS, Linux | `install.sh` | The one-command install script. On Linux, it can also install a `mytwig-<version>-linux-<arch>.tar.gz` file in the same folder |
| Windows | `install.ps1` | The one-command install script |
| (all) | `SHA256SUMS` | SHA-256 checksums of the installers, archives and scripts. The file shows spaces in the names, where GitHub shows dots |
| (all) | `update-<platform>.json`, `mytwig-<version>-<platform>.tar.gz` | The auto-updater uses these files. Scoop also uses the Windows archive. You do not have to download these files. |

#### macOS

1. Download the disk image for your Mac:
   - Apple silicon (M1 and later): `MyTwig <version> arm64.dmg`
   - Intel: `MyTwig <version> amd64.dmg`
2. Open the disk image.
3. Drag **MyTwig** into **Applications**.
4. Open MyTwig from **Applications**.

> **NOTE:** If you do not know the chip of your Mac, select Apple menu → **About This Mac**. Apple silicon shows **Chip: Apple M…**. Intel shows **Processor: … Intel …**.

> **NOTE:** The first launch needs one more procedure. See the section below.

##### First launch: "Open Anyway"

This build **does not have an Apple Developer ID signature, and Apple did not notarize it**. It has only an ad-hoc signature. Thus, Gatekeeper blocks MyTwig the first time that you open it. This is normal. To let MyTwig open, do the procedure for your macOS version.

**macOS 15 Sequoia and later**

1. Double-click MyTwig.
2. When a dialog tells you that Apple could not verify MyTwig, click **Done**.
3. Open **System Settings → Privacy & Security**.
4. Scroll to **Security**.
5. Next to the message about "MyTwig", click **Open Anyway**.
6. Enter your password or use Touch ID to confirm.
7. Open MyTwig again.
8. Click **Open**.

**macOS 12–14**

1. In **Applications**, Control-click (or right-click) MyTwig.
2. Select **Open**.
3. In the dialog, click **Open**.

You can also use **System Settings → Privacy & Security → Open Anyway**, as in the procedure above.

You must do this procedure only one time. If you trust the download, you can run this command in Terminal instead:

```sh
xattr -dr com.apple.quarantine /Applications/MyTwig.app
```

> **CAUTION:** Run this command only if you trust the download. The command removes the quarantine flag from MyTwig.

#### Windows

1. Run the installer for your device:
   - x64: `MyTwig Setup <version> amd64.exe`
   - ARM: `MyTwig Setup <version> arm64.exe`
2. If **Microsoft Defender SmartScreen** shows a warning, click **More info**.
3. Click **Run anyway**.

> **NOTE:** The installer does not have a code signature yet. Thus, SmartScreen can show a warning.

MyTwig installs for your user only, in `%LOCALAPPDATA%\Programs\MyTwig`. The installer adds a Start menu shortcut. If you select this option, it also adds a desktop shortcut. To uninstall MyTwig, use **Settings → Apps**.

#### Linux

**Option A: install script (recommended, updates itself).** The script installs MyTwig into `~/.local` for your user. It does not need root. It adds a desktop entry. After the installation, the app can update itself:

```sh
curl -fsSL https://github.com/HeroSizy/mytwig-releases/releases/latest/download/install.sh | sh
```

You can also install MyTwig from local files:

1. Download `install.sh` into a folder.
2. Download the `mytwig-<version>-linux-<arch>.tar.gz` file for your architecture into the same folder.
3. In that folder, run `sh install.sh`.

To remove MyTwig, run `sh install.sh --uninstall`. This command keeps your settings.

> **NOTE:** The script does not install WebKitGTK. If your computer does not have WebKitGTK, the script shows the command that installs it.

**Option B: Debian/Ubuntu package.**

```sh
sudo apt install ./mytwig_<version>_amd64.deb   # or _arm64.deb
```

The package installs MyTwig in `/opt/mytwig`.

> **NOTE:** The package **does not update itself**. To update MyTwig, install the newer `.deb`.

## Updates

MyTwig uses this repository to find new versions. It does a check when it starts, if the last check is more than 30 minutes old. Then it does a check every 30 minutes. The update procedure has these steps:

1. MyTwig downloads `update-<platform>.json` from the **latest release** of this repository. The platforms are `darwin-arm64`, `darwin-amd64`, `windows-amd64`, `windows-arm64`, `linux-amd64` and `linux-arm64`. Each build reads only its own file. Thus, an Apple silicon Mac always uses the arm64 build.
2. If the manifest shows a newer version, MyTwig shows this version and its release notes in a window. You can install it, skip that version, or get a reminder later.
3. If you install the update, MyTwig downloads the archive from the manifest. If a smaller delta from your version is available, MyTwig downloads the delta. Then MyTwig examines the size of the archive. It also examines the **Ed25519 signature with the public key in the app**. MyTwig refuses an update without a signature from the MyTwig key.
4. MyTwig puts the new version next to the old version. If this fails, MyTwig restores the old version. MyTwig uses the new version when it starts the next time, or when you click **Relaunch**.

MyTwig downloads updates over HTTPS from GitHub. You do not need an account or a token. MyTwig sends no data about you or your repositories.

To change these settings, go to **Settings → General → Updates**. There you can:

- Start or stop the background checks.
- Select if MyTwig installs updates without a question.
- Do a check now.

On macOS, you can also use **MyTwig → Check for Updates…**. The same Settings row shows the current version and the time of the last check.

Some installs cannot update themselves, and Settings tells you this. These installs are:

- Development builds.
- The `.deb` install, because it is in `/opt` and root owns it.
- A copy that you cannot write to. An example is an app in `/Applications` on a macOS account without administrator rights.

Installs from Homebrew, Scoop or winget can also update themselves. But then the package manager continues to show the version that it installed. Thus, use the package manager to update these installs (see [Package managers](#package-managers)).

## Privacy

MyTwig has no analytics and no server of its own. It connects to your Git remotes and to the forges where you have an account (GitHub, GitLab, Gitea/Forgejo, Bitbucket). It also connects to avatar services, to your AI provider (if you have one), and to GitHub for updates. **Settings → Privacy** shows all the hosts that MyTwig connects to. MyTwig keeps tokens in the system keychain: Keychain on macOS, Credential Manager on Windows, and the Secret Service on Linux.

**Crash reports are optional and off by default.** At the first launch, MyTwig asks you one time, and the box is clear. You can change this later in **Settings → Privacy**. If you allow crash reports, MyTwig sends a report of each crash to the developer through [Sentry](https://sentry.io). A report contains only this data:

- the versions of MyTwig, git and your OS, and the platform (for example, `darwin-arm64`);
- the location of the crash in the MyTwig code: function names, file names and line numbers;
- the error message, without paths, URLs, emails, quoted text and hashes;
- the names of the last MyTwig commands that you ran (for example, "Fetch All");
- a random install ID. MyTwig uses this ID only to tell one install from a different install.

A report never contains your code, file paths, branch names, remotes, commit messages, names or emails. If crash reports are off, MyTwig sends nothing. It keeps a crash report only on your computer. If you allow crash reports later, MyTwig sends that report then. **Settings → Privacy → View Last Report…** shows exactly what MyTwig sends, or sent.

## Feedback

Report bugs and send feedback in [GitHub Issues](https://github.com/HeroSizy/mytwig-releases/issues).

## License and terms

You can use MyTwig free of charge. All rights reserved.

MyTwig includes third-party fonts (Inter, IBM Plex Sans, JetBrains Mono, Fira Code, Cascadia Code, Caveat, Ma Shan Zheng). Each font has the SIL Open Font License 1.1.

Copyright © 2026 HeroSizy.
