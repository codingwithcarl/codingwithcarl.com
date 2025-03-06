+++ 
draft = false
date = 2021-10-19T08:46:54-04:00
title = "Easy Automation"
description = "Simple scripts to create workspaces"
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++

In two of my private GitHub repositories, I have a collection of scripts that I personally use to automate repetitive tasks. The main use case is to create "workspaces" as fast as  possible. 

For example, in Linux, the following script called **dashboard.sh** opens my email, calendar, and to-do list. 

```bash
#!/bin/bash
google-chrome --new-window calendar.google.com
google-chrome --new-window mail.google.com keep.google.com
exit
```

This is assigned to a keybind in AwesomeWM for quick access. You can also do the same in Microsoft Windows with a batch script, **dashboard.bat**, and send it to the Desktop as a shortcut.

```batch
start chrome /new-window https://mail.google.com https://keep.google.com/
start chrome /new-window https://calendar.google.com/
exit
```

In case you're wondering, yes, Google Chrome can already do this itself by assigning pages to open up when the application is launched. However, this method is more versatile as it can be used with any category of pages plus applications. It's also less of a memory hog, as you are able to close these running processes when they are not used and with the ability to quickly spin them up again.

Here's another example which docks my laptop to two external monitors with xrandr on Linux. Again, easy to do with a key press:

```bash
#!/bin/sh
xrandr --output HDMI-0 --mode 2560x1440 --rate 74.97 --pos 2560x0 --rotate normal --output DP-1 --primary --mode 2560x1440 --rate 74.97 --pos 0x0 --rotate normal --output LVDS-0 --off --output VGA-0 --off  --output DP-0 --off

```

Need to set up a development workspace in Microsoft Windows? This will open Visual Studio Code, Outlook, Teams (or slack), and two file explorer windows.

```batch
start chrome /new-window https://stackoverflow.com/
start outlook 
start "" "C:\Users\Carl\AppData\Local\Microsoft\Teams\Update.exe" --processStart "Teams.exe"
start "" "C:\Users\Carl\AppData\Local\slack\slack.exe" 
%SystemRoot%\explorer.exe "C:\Users\Carl\dev"
%SystemRoot%\explorer.exe "C:\Users\Carl\Downloads"
code
exit
```

You can substitute any of the executables to open any application. 

Here's another example for Linux systems. This example uses the nautilus file manager and shows how to open an AppImage.

```bash
google-chrome --new-window https://docs.docker.com/
codium /home/z/dev/project/
gnome-terminal
/home/z/AppImages/marktext/marktext-x86_64.AppImage
nautilus /home/z/dev/project1
exit
```

Some other workspace ideas:

- College courses (I used these a lot across different subjects)

- Paying bills (open your bank accounts, credit card sites, and Excel)

- Job Applications 

- Social Media

- News