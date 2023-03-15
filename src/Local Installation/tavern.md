---
order: 10
icon: ":desktop_computer:"
title: TavernAI
---

TavernAI is an atmospheric front-end that connects to KoboldAI, NovelAI, or OpenAI (but doesn't run the models itself, as opposed to KoboldAI and Oobabooga's TextGen). 

![](/static/TavernAI.PNG)


## Installation
Installing TavernAI is simple. It *officially* supports the following operating systems:
- Windows x64
- Linux x64
- MacOS (Darwin x64)

### Windows Installation

Download TavernAI and run the installer:

[!file TavernAI](https://sourceforge.net/projects/tavernaimain/files/TavernAI.rar/download)

!!!info
You'll need a program such as [7zip](https://www.7-zip.org/download.html){target="blank"} to extract the installer.
!!!

### Linux/MacOS Installation

If you're on Linux, an automatic installer script is available in the main Tavern repo now. It's still recommended to use your package manager, as the script might mess up if your environment is very custom-made (or you're using NixOS). If you already have nodejs installed, or would like to use the script, please skip the `nodejs` installation section.

#### Requirements
- nodejs
- git

#### Installation

- Download `nodejs` via your package manager of choice.
```
sudo pacman -S nodejs               # Arch Linux
sudo apt install nodejs             # Debian/Ubuntu
doas apk add nodejs-current         # Alpine Linux
sudo dnf install nodejs:19/common   # Fedora/RHEL
sudo emerge nodejs                  # Gentoo
brew install node                   # MacOS
sudo xbps-install -Sy nodejs        # Void Linux
```

- Clone the repo
```
git clone https://github.com/TavernAI/TavernAI && cd TavernAI
```

- Run TavernAI
```
npm i && node server.js
```

- Connect your KoboldAI instance (works both locally and with Colab)

![](/static/tavern-local1.png)![](/static/tavern-local2.png)

!!!info The API URL
If you're running KoboldAI locally, all you need to paste in there is `http://localhost:5000/api`. If you're using Google Colab, copy your remote URL instead. If it ends with a # or new_ui, remove them and replace them with /api. If they don't, simply adding /api will suffice.
!!!

!!!success You're done!
You can now start using TavernAI! TavernAI uses Character Cards, which are images (PNG and WEBP) that can be imported to Tavern as Characters. Tavern 1.3 by default has a list of community-added Characters in the home page (provided you have an internet connection). You can also find new characters in the unofficial [Discord server](https://discord.com/invite/pygmalionai).