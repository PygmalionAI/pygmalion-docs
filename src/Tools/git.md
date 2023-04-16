---
order: 10
icon: gear
title: Git
---

# What's Git and do I need it?

Git is a popular version control system used by software developers to manage their code. It allows developers to track changes to their code over time, collaborate with others, and revert back to previous versions if needed.   
Git gives you access to useful commands, such as `git clone`. You can use it to create a local copy of a remote repository, including all its files and history, on your local machine.

!!!info
Many of our tutorials use Git, so you should consider installing it by following the instructions below.
!!!

- [Windows x64](https://docs.alpindale.dev/tools/git/#windows)
- [Linux x64]()
- [MacOS (Darwin x64)](https://docs.alpindale.dev/tools/git/#macos)


## Windows

You can easily install Git by following a few simple steps. Start by navigating to your desktop and then hold down the Shift key while right-clicking. From the context menu, select the option to `Open PowerShell Window here`.

![](/static/OpenPSWindows.PNG)

In the PowerShell, run this command : `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser` (Copy paste it into the PowerShell and press enter).

You should get a message asking you if you want to change the "execution policy", press `y` then enter.

![](/static/PSExecutionPolicy.PNG)

Once it's done, run those two command one by one :

`irm get.scoop.sh | iex`

`scoop install git`

!!!success You're done
Git should be properly installed now.
!!!

## MacOS
To make things easier, we gonna use "Homebrew".

First you gonna open the Terminal application on your Mac. You can find it in the "Utilities" folder within the "Applications" folder.

Then you gonna have to run this command in the terminal :

 `$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)` (Copy paste it in the terminal and press enter).

Once it's done, simply run `$ brew install git`

At this point, you've installed Git on your Mac. You can now verify by running this command in your terminal: `$ Git --version`

