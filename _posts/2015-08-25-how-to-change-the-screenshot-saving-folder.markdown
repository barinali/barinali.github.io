---
author: barinali
comments: true
date: 2015-08-25 21:58:25+00:00
layout: post
link: http://blog.alibarin.com.tr/how-to-change-the-screenshot-saving-folder
permalink: /how-to-change-the-screenshot-saving-folder
title: How to Change the Screenshot Saving Folder
meta_description: How to change the screenshot saving folder on MacOS
categories:
- Uncategorised
tags:
- capturing folder
- change
- mac os
- saving folder
- screenshots
---

cmd+shift+3 (capture all screen to save) or cmd+shift+4 (capture part of screen to save) are two of the commonly used shortcuts for who are Mac OS user.

I often use these shortcuts. But I wasn't happy because of these screenshots keep place on my desktop. I learned the saving folder can be changed and how can I change it.

We follow a few steps for the changing. We can apply the following on terminal for changing path as ~/Desktop/Screenshots/;

    mkdir ~/Desktop/Screenshots/
    defaults write com.apple.screencapture location ~/Desktop/Screenshots/
    killall SystemUIServer

**p.s.**: If you already created a folder for this action, you don't need apply _mkdir_ command which is on highlighted line.
