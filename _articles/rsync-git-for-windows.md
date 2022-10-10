---
title: 利用 Git for Windows 使用 rsync
description: 在 Windows 上利用 Git 的 MSYS2 安装 rsync。

mermaid: true
---

# 利用 Git for Windows 使用 rsync

> 2022年10月9–10日。
>
> 本文的其它版本：[WriteBug.com](https://www.writebug.com/explore/article/YSCCk7Vt)。

## 0 这都是啥

- **[Git for Windows](https://gitforwindows.org/)**

  Git 需要一些 POSIX 方面的基础设施，很难直接在 Windows 上运行。
  
  [MSYS2](https://www.msys2.org/)（≈ <u>m</u>inimal <u>sys</u>tem 2）可以在 Windows 上模拟一层 POSIX，解决了这个困难。Git for Windows 团队从 2.x 开始选择使用它来实现。
  
  <div class="mermaid">
  flowchart LR
  git[Git for<br> Windows] --> msys2["MSYS2<br>（修改版）"] -.-> POSIX -.-> Windows
  </div>
  
  总而言之，Git for Windows 内置的环境可以运行一些原本需要 POSIX 的程序。
  
  有些场景下，借用 Git for Windows 里的环境比使用 WSL（Windows Subsystem for Linux）更划算。
  
- **[rsync](https://rsync.samba.org/)**

  rsync 是一种文件传输／同步工具。

  <div class="mermaid">
  flowchart LR
  硬盘 <-->|rsync| 你的电脑 <-->|rsync| 远程服务器
  
  subgraph 硬盘
      direction LR
  
      md_硬盘[ReadMe.md]
      cargo_硬盘[Cargo.toml]
      other_硬盘["…"]
  end
  
  subgraph 你的电脑
      direction LR
  
      md_你的电脑[ReadMe.md]
      cargo_你的电脑[Cargo.toml]
      other_你的电脑["…"]
  end
  
  subgraph 远程服务器
      direction LR
  
      md_远程服务器[ReadMe.md]
      cargo_远程服务器[Cargo.toml]
      other_远程服务器["…"]
  end
  </div>

  情况合适时，rsync 不会死板地复制所有文件，而只传输真正有用的部分。

---

本文介绍如何利用 Git for Windows 中的 MSYS2 安装 rsync。

<div class="mermaid">
flowchart LR
git --> msys2["MSYS2"] -.-> POSIX -.-> Windows

rsync:::goal --> msys2

classDef goal fill:orange;
</div>

## 1 安装 Zstandard

Zstandard（`zstd`）是一种压缩算法。MSYS2 较新版的包都用这种格式（`*.zst`）发布，为了解压这些压缩包，我们需要先安装`zstd`。

> 你也可不按这里的方法，而用其它工具解压`*.zst`，比如[`pip install zstandard`](https://pypi.org/project/zstandard/)。

1. **下载安装包**

   前往 [Releases · facebook/zstd](https://github.com/facebook/zstd/releases/latest)，下载 Assets → `zstd-○○-○○.zip`。（例如[`zstd-v1.5.2-win64.zip`](https://github.com/facebook/zstd/releases/download/v1.5.2/zstd-v1.5.2-win64.zip)）

2. **解压以安装**

   可用任意方式解压到任意地方。

3. **确认成功安装**

   打开任意终端（PowerShell／Git Bash／…），查看`zstd`的版本（version）。

    ```shell
    $ /path/to/zstd -V
    *** zstd command line interface 64-bits v1.○.○, by Yann Collet ***
    ```

   > 如果你以后还打算用`zstd`，可以给它设置别名，或加入`PATH`。

之后我们就能用`zstd -d □□`解压（decompress）文件了。

## 2 安装 rsync

MSYS2 本身有包管理器，但 Git for Windows 中的是精简版，我们需要手动安装。

1. **下载安装包**

   前往 [MSYS2 仓库](https://repo.msys2.org/msys/x86_64/)，找到`rsync-○○.pkg.tar.zst`，下载。（例如[`rsync-3.2.6-1-x86_64.pkg.tar.zst`](https://repo.msys2.org/msys/x86_64/rsync-3.2.6-1-x86_64.pkg.tar.zst)）

2. **解压安装包**

   可用任意方式解压到任意地方。

   如果你按上面的方法安装了 Zstandard，可以打开任意终端，如下操作。

   ```bash
   $ mkdir rsync
   $ cd ./rsync
   $ mv /path/to/rsync-○○.pkg.tar.zst .
   
   # ↓ 解压第一层：*.tar.zst → *.tar
   $ zstd -d /path/to/rsync-○○.pkg.tar.zst
   # ↓ 解压第二层：*.tar → ./usr/*
   $ tar -xvf rsync-○○.pkg.tar
   
   # ↓ （可选）确认解压成功
   $ ls usr/
   bin/ lib/ share/
   ```

3. **移动到合适位置**

   将解压出的`/usr/bin/rsync.exe`移动到 Git 安装目录的`/usr/bin/`。

   可用任意方法移动，例如使用任意终端`mv`。

   ```shell
   $ mv /path/to/rsync/usr/bin/rsync.exe 'C:/Program Files/Git/usr/bin/'
   ```

   > 如果你使用 Git Bash，可直接写`/usr/bin/`。

   之后可删除解压出来的其它文件。

4. **安装 DLL**

   仿照以上操作安装`libzstd`、`libxxhash`：逐一下载、解压、移动。

   全部完成后，可以卸载（按上面的方法安装的）Zstandard。（直接删除`zstd.exe`）

5. **确认成功安装**

   打开 Git Bash，如下操作。

   ```bash
   $ rsync
   rsync  version 3.2.3  protocol version 31
   Copyright (C) 1996-2020 by Andrew Tridgell, Wayne Davison, and others.
   Web site: https://rsync.samba.org/
   ……
   ```

至此，应当可以在 Git Bash 中使用 rsync。具体使用方法请参考[手册](https://download.samba.org/pub/rsync/rsync.1)。

## 3 给其它终端配置 rsync

> 如果你只准备在 Git Bash 中用 rsync，无需此步。

### 设置别名

Git 中的软件可以在 Git Bash 外直接使用，rsync 同理。

```powershell
# 例如在 PowerShell 中使用 nano
> New-Alias -Name nano -Value "C:\Program Files\Git\usr\bin\nano.exe"
> nano -V
 GNU nano, version 6.4
 ……
```

这里以 PowerShell 为例。

1. **编辑[`$PROFILE`](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_profiles)，添加以下内容。**

   ```powershell
   New-Alias -Name rsync -Value "C:\Program Files\Git\usr\bin\rsync.exe"
   ```

2. **重启终端。**

3. **确认成功设置。**

   ```powershell
   > rsync
   rsync  version 3.2.3  protocol version 31
   Copyright (C) 1996-2020 by Andrew Tridgell, Wayne Davison, and others.
   Web site: https://rsync.samba.org/
   ……
   ```

### 告知 rsync 仍使用 Git 中的 SSH

Windows 功能中的 SSH（设置 → 应用 → 应用和功能 → 可选功能 → OpenSSH 客户端）与 Git Bash 中的并不完全相同，可能与 rsync 存在兼容性问题，例如 [connection unexpectedly closed](https://github.com/PowerShell/Win32-OpenSSH/issues/1869)。

```bash
# Git Bash
$ ssh -V
OpenSSH_9.0p1, OpenSSL 1.1.1q  5 Jul 2022
```

```powershell
# PowerShell 等其它终端
> ssh -V
OpenSSH_for_Windows_8.1p1, LibreSSL 3.0.2
```

为此，我们需要告知 rsync 使用 Git 中的 SSH。

rsync 支持通过[选项`--rsh`](https://download.samba.org/pub/rsync/rsync.1#opt-e)和[环境变量`RSYNC_SSH`](https://download.samba.org/pub/rsync/rsync.1#RSYNC_RSH)设置使用什么 shell。

```bash
# 例如调试 rsync 时，可使用 verbose 模式的 ssh。
$ rsync --rsh 'ssh -v' ……
```

由于 Git for Windows 的安装目录（很可能）包含空格，而命令行选项会经过层层翻译，最后鬼都不知道变成什么。所以建议采用环境变量。

<div class="mermaid">
flowchart LR
PowerShell -->|"rsync --rsh …"| rsync
rsync -->|"ssh …"| ssh -.-> ? -.-> ?? -.-> ????
</div>

这里以 PowerShell 为例。

> PowerShell 是 VS Code `tasks.json`中任务使用的默认终端。

1. **编辑[`$PROFILE`](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_profiles)，添加以下内容。**

   ```powershell
   # We need redundant quotes to avoid from splitting “Program Files”.
   $env:RSYNC_RSH = 'C:\"Program Files"\Git\usr\bin\ssh.exe'
   ```

   > 环境变量仍可能发生翻译，试验表明，不能写`'""C:\Program Files\Git\usr\bin\ssh.exe""'`。

2. **重启终端。**

## 参考

- [Seunghyun Chae](https://shchae7.medium.com/), [*How to use rsync on Git Bash*](https://shchae7.medium.com/how-to-use-rsync-on-git-bash-6c6bba6a03ca), [Medium](https://medium.com/), 2021-01-03.
- [nextgentech](https://serverfault.com/users/212162/nextgentech), [the answer](https://serverfault.com/a/872557/982180), [*windows - Using rsync from msysgit for binary files*](https://serverfault.com/questions/310337/using-rsync-from-msysgit-for-binary-files), [Server Fault](https://serverfault.com), 2019-08-07.
- [git-for-windows/git](https://github.com/git-for-windows/git) Wiki, [*Home*](https://github.com/git-for-windows/git/wiki/Home/b2f4a75dee0e112d777ebce278bde452f0550799), [GitHub](https://github.com/), 2020-06-18.