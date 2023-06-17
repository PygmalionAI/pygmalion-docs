---
order: 10
icon: mark-github
title: Git
---

# What's Git and do I need it?

Git is a popular version control system used by software developers to manage their code. It allows developers to track changes to their code over time, collaborate with others, and revert back to previous versions if needed.   
Git gives you access to useful commands, such as `git clone`. You can use it to create a local copy of a remote repository, including all its files and history, on your local machine. The most useful command for an end-user is `git pull`, which allows you to update a cloned repository easily without having to re-download the zip file and merging it into your cloned folder.

!!!info
Many of our tutorials use Git, so you should consider installing it by following the instructions below.
!!!

- [Windows x64](https://docs.pygmalion.chat/tools/git/#windows)
- [MacOS (Darwin x64)](https://docs.pygmalion.chat/tools/git/#macos)
- [Linux x64](https://docs.pygmalion.chat/tools/git/#linux)


## Windows

Installation is very simple. Open the Start Menu and search for `PowerShell`. Right-click on it and Open as Administrator. Once the blue PowerShell window pops up, simply type these two commands in order and **press enter to execute them**:

1. Install `git`:
```bash
winget install -e --id Git.Git
```

2. Install `git lfs`
```bash
winget install -e --id GitHub.GitLFS
```

3. Close PowerShell.

<!-- You can easily install Git by following a few simple steps. Start by navigating to your desktop and then hold down the Shift key while right-clicking. From the context menu, select the option to `Open PowerShell Window here`.

![](/static/OpenPSWindows.PNG)

In the PowerShell, run this command : `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser` (Copy paste it into the PowerShell and press enter).

You should get a message asking you if you want to change the "execution policy", press `y` then enter.

![](/static/PSExecutionPolicy.PNG)

Once it's done, run those two command one by one:

`irm get.scoop.sh | iex`

`scoop install git`

!!!success You're done
Git should be properly installed now.
!!! -->

## macOS
To make things easier, we will use "Homebrew", a commandline software installer for macOS.

First you will need to open the Terminal application on your Mac. You can find it in the "Utilities" folder within the "Applications" folder.

Then run this command in the terminal (Copy paste it in the terminal and press enter):

 ```
 $ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)
 ``` 

Once it's done, simply run `brew install git`

At this point, you've installed Git on your Apple Silicon. You can now verify by running this command in your terminal: `$ Git --version`


## Linux

I shouldn't have to explain this to you, Linux user. `git` is on every package manager. However, I like extensive documentation, so I will list instructions for all distros.

If you're unsure what your distro is, run `uname -v | awk '{print $4}'`.
- Install `git` and `git-lfs`:

```
sudo pacman -S git git-lfs                # Arch/Manjaro/Endeavour
sudo apt install git git-lfs              # Debian/Ubuntu/Mint
doas apk add git git-lfs                  # Alpine Linux
sudo dnf install git git-l                # Fedora/RHEL
sudo emerge dev-vcs/git dev-vcs/git-lfs   # Gentoo
sudo xbps-install git git-lfs             # Void Linux
sudo zypper in git-core git-lfs           # OpenSUSE
nix-env -iA nixos.git nixos.git-lfs       # NixOS
nix-env -iA nixpkgs.git nixpkgs.git-lfs   # Nix
```