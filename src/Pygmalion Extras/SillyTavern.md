---
order: 10000
icon: comment-discussion
title: SillyTavern
---
SillyTavern is a user interface you can install on your computer (and Android phones) that allows you to interact with text generation AIs and chat/roleplay with the characters you or the community create.

!!!info
SillyTavern is just a UI; you will need to connect it to a backend: [KoboldAI](https://docs.alpindale.dev/local-installation-(gpu)/kobold/) or [TextGen WebUI](https://docs.alpindale.dev/local-installation-(gpu)/oobabooga/).
!!!

![](/static/SillyTavern.PNG)

## Installation
Installing SillyTavern is simple. It supports the following operating systems:
- [Windows x64](https://docs.alpindale.dev/pygmalion-extras/sillytavern/#windows-installation)
- [Linux x64](https://docs.alpindale.dev/pygmalion-extras/sillytavern/#linuxmacos-installation)
- [MacOS (Darwin x64)](https://docs.alpindale.dev/pygmalion-extras/sillytavern/#linuxmacos-installation)
- [Android (aarch64)](https://docs.alpindale.dev/pygmalion-extras/sillytavern/#android-installation)


### Windows Installation

First, you will need to install [Node.js](https://nodejs.org/en/download/current){target="blank"}.

![](/static/NodeJSWindows.PNG)

Just open the installer, and click on Next, Next, etc.. (You don't have to change anything in the installer)
Once Node.JS is installed, you can download Silly Tavern !

!!!info
You'll need [Github Desktop](https://central.github.com/deployments/desktop/desktop/latest/win32) to clone the repository.
!!!

After installing GitHub Desktop, click on `Clone a repository from the internet...`. (Note that you do not need to create an account for this step)

![](/static/GUI-File.PNG)

On the menu, go into the `URL` tab, enter this url `https://github.com/Cohee1207/SillyTavern` and click `clone`.

!!!info
You can change the `Local path` to change where SillyTavern is going to be downloaded.
!!!

![](/static/GUI-Clone.PNG)


To open SillyTavern, just go into the folder where you cloned the repository, and double click on the start.bat file. 
!!!info
By default, the repository will be clone here : `C:\Users[Your Account Name]\Documents\GitHub\SillyTavern`
!!!

![](/static/StartBat.PNG)

<!-- Open PowerShell (you can search for it in the start menu) and type in `winget install -e --id OpenJS.NodeJS`. Once it's finished, close PowerShell.

You can confirm whether NodeJS is installed by running `node -v` in PowerShell.

To run SillyTavern, all you'll need to do is open PowerShell again and running `npx sillytavern@latest`. This will open SillyTavern in your browser. You can re-launch SillyTavern anytime by running `npx sillytavern@latest`. -->

If everything is working, the CMD should look like this and a SillyTavern tab should be open in your browser.

![](/static/STcmd.PNG)

!!!warning
You still have to [connect](https://docs.alpindale.dev/local-installation-(gpu)/sillytavern/#connect-sillytavern) it!
!!!


### Linux/MacOS Installation

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

#### Installation (with `npx`)

Run `npx sillytavern@latest`. You can re-open it anytime by running the command again.


#### Installation (manual)

- Clone the repo
```
git clone -b dev https://github.com/Cohee1207/SillyTavern && cd SillyTavern
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
pkg install nodejs openssl
```

Download Silly Tavern:
```bash
git clone -b dev https://github.com/Cohee1207/SillyTavern && cd SillyTavern
```
!!!warning fatal: destination path 'SillyTavern' already exists
If you receive the above error, it means you've already downloaded SillyTavern before. In that case, you can simply update it. Change directories to SillyTavern by running `cd SillyTavern`, and then updating it by running `git pull`. 
!!!

<!-- Run SillyTavern:
```bash
npx sillytavern@latest
```
 -->
 Run SillyTavern:
```bash
npm i && node server.js
```

!!!info
You can run SillyTavern again by simply opening Termux and entering the command above!
!!!

#### Connect to Horde
![Recommended for Phone Users](/static/quickstart1.png)

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


