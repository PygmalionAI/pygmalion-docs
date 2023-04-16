---
order: 1
icon: ":desktop_computer:"
title: SillyTavern
---
SillyTavern is a user interface you can install on your computer (and Android phones) that allows you to interact with text generation AIs and chat/roleplay with the characters you or the community create.

!!!info
SillyTavern is just a UI; you will need to connect it to a backend: [KoboldAI](https://docs.alpindale.dev/local-installation-(gpu)/kobold/), [TextGen WebUI](https://docs.alpindale.dev/local-installation-(gpu)/oobabooga/) or [Google Colab](https://docs.alpindale.dev/cloud-installation/koboldai/).
!!!

![](/static/SillyTavern.PNG)

## Installation
Installing SillyTavern is simple. It supports the following operating systems:
- [Windows x64](https://docs.alpindale.dev/local-installation-(gpu)/sillytavern/#windows-installation)
- [Linux x64](https://docs.alpindale.dev/local-installation-(gpu)/sillytavern/#linuxmacos-installation)
- [MacOS (Darwin x64)](https://docs.alpindale.dev/local-installation-(gpu)/sillytavern/#linuxmacos-installation)
- [Android (aarch64)](https://docs.alpindale.dev/local-installation-(gpu)/sillytavern/#android-installation)


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

Install `nvm` (NodeJS Version Manager) by running the following command in Terminal:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```

Run this to make `nvm` usable:

```bash
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```

Install NodeJS by running the following command:

```bash
nvm install node
```

#### Installation


- Clone the repo
```
git clone -b dev https://github.com/Cohee1207/SillyTavern && cd TavernAI
```

- Run TavernAI
```
npm i && node server.js
```

### Android Installation

- Install [Termux](https://f-droid.org/repo/com.termux_118.apk).
- Run the following commands inside Termux, in order:

Update repos/packages:
```bash
pkg update && pkg upgrade
```

Install NodeJS and git:
```bash
pkg install nodejs openssl git
```

Download Silly Tavern:
```bash
git clone -b dev https://github.com/Cohee1207/SillyTavern && cd Tavern
```
!!!warning fatal: destination path 'SillyTavern' already exists
If you receive the above error, it means you've already downloaded SillyTavern before. In that case, you can simply update it. Change directories to SillyTavern by running `cd SillyTavern`, and then updating it by running `git pull`. 
!!!

Run SillyTavern:
```bash
npm i && node server.js
```
## Connect SillyTavern

![](/static/STconnect.PNG)

!!!info The API URL
If you're running KoboldAI locally, all you need to paste in there is `http://localhost:5000/api`. If you're using Google Colab, copy your [remote URL](https://docs.alpindale.dev/cloud-installation/koboldai/#using-the-remote-url-to-connect-sillytavern) instead. If it ends with a # or new_ui, remove them and replace them with /api. If they don't, simply adding /api will suffice.
!!!

!!!info Note for Mobile Users
Please switch to `Desktop Mode` in your browser settings.
!!!

!!!success You're done!
You can now start using SillyTavern! SillyTavern uses Character Cards, which are images (PNG and WEBP) that can be imported to Tavern as Characters. You can also find new characters in the unofficial [Discord server](https://discord.com/invite/pygmalionai).


