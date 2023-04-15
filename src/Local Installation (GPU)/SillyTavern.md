---
order: 1
icon: ":desktop_computer:"
title: SillyTavern
---
SillyTavern is a user interface you can install on your computer (and Android phones) that allows you to interact text generation AIs and chat/roleplay with characters you or the community create.

!!!info
SillyTavern is just an UI, you need to connect it to a backend ([KoboldAI](https://docs.alpindale.dev/local-installation-(gpu)/kobold/), [TextGen WebUI](https://docs.alpindale.dev/local-installation-(gpu)/oobabooga/) or a [Google Colab] that run the model of your choice (We'll see that later)
!!!

![](/static/SillyTavern.PNG)

## Installation
Installing SillyTavern is simple. It *officially* supports the following operating systems:
- [Windows x64](https://docs.alpindale.dev/local-installation-(gpu)/sillytavern/#windows-installation)
- [Linux x64](https://docs.alpindale.dev/local-installation-(gpu)/sillytavern/#linuxmacos-installation)
- [MacOS (Darwin x64)](https://docs.alpindale.dev/local-installation-(gpu)/sillytavern/#linuxmacos-installation)


### Windows Installation

First, you gonna need to install [Node.js](https://nodejs.org/en/download/current){target="blank"}.

![](/static/NodeJSWindows.PNG)

Just open the installer, and click on Next, Next, etc.. (You don't have to change anything in the installer)

Once Node.JS is installed, you can download Silly Tavern

[!file SillyTavern](https://github.com/Cohee1207/SillyTavern/archive/refs/heads/main.zip)

!!!info
You'll need a program such as [7zip](https://www.7-zip.org/download.html){target="blank"} or [WinRAR](www.win-rar.com/predownload.html){target="blank"} to extract the folder.
!!!


Extract it in the folder of your choice (right click -> extract here).

To open SillyTavern, just double click on the start.bat file. 
![](/static/StartBat.PNG)

If everything is working, the CMD should look like this and a SillyTavern tab should be open in your browser.

![](/static/STcmd.PNG)

!!!danger
You still have to [connect](https://docs.alpindale.dev/local-installation-(gpu)/sillytavern/#connect-sillytavern) it !
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
git clone https://github.com/Cohee1207/SillyTavern && cd TavernAI
```

- Run TavernAI
```
npm i && node server.js
```


## Connect SillyTavern

![](/static/STconnect.PNG)

!!!info The API URL
If you're running KoboldAI locally, all you need to paste in there is `http://localhost:5000/api`. If you're using Google Colab, copy your [remote URL](https://docs.alpindale.dev/cloud-installation/koboldai/#using-the-remote-url-to-connect-sillytavern) instead. If it ends with a # or new_ui, remove them and replace them with /api. If they don't, simply adding /api will suffice.
!!!

!!!success You're done!
You can now start using SillyTavern! SillyTavern uses Character Cards, which are images (PNG and WEBP) that can be imported to Tavern as Characters. You can also find new characters in the unofficial [Discord server](https://discord.com/invite/pygmalionai).


