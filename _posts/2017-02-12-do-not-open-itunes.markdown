---
author: barinali
comments: true
date: 2017-02-12 16:00:00+00:00
layout: post
link: http://blog.alibarin.com.tr/do-not-open-itunes/
permalink: /do-not-open-itunes
title: Don't Open iTunes!
meta_description: Don't Open iTunes!
categories:
- Uncategorized
tags:
- macOS
- Sierra
- Spotify
- iTunes
- Media keys
- Keyboard shortcuts
excerpt: I don't love using iTunes for listening to music!
---

I do like listening to music while working. But there is a problem with that. When I want to listen to music, I press the ⏯ button. But it opens iTunes on Mac! Because Spotify always isn’t open and I don’t like using <a href="https://support.apple.com/kb/PH21985?locale=en_US" title="Open items automatically when you log in">login items</a>. So I'd love to change this behaviour. In order to achieve our objective, we need to follow some steps.

## Remove iTunes Helper from Launch Agents

For doing this, you need to use this command on your CLI; `launchctl unload -w /System/Library/LaunchAgents/com.apple.rcd.plist`. What does the command do? It removes iTunes launch agent from between <a href="http://www.launchd.info/" title="What is launchd?">Launch Agents</a>.

## You have iTunes-less Launch! Hooray!

We got rid of iTunes issue. But now Spotify won’t open when you press ⏯ media key on your keyboard if it’s not in login items. In shortly, you can resolve this issue by adding Spotify to your login items.


## Is there something more?

I’d like to say that you can add Spotify Helper to your Launch Agents. But it seems like not possible for now. Besides that, you may want to check <a href="https://github.com/beardedspice/beardedspice" title="BeardedSpice">BeardedSpice</a> out to manage all media stuffs on MacOS.

## Open Spotify with a custom shortcut

It's possible with automator and keyboard shortcuts. You can define a service which opens Spotify on Automator. Then you can define a keyboard shortcut to run that service. For more information, click <a href="https://forums.macrumors.com/threads/can-i-assign-f8-the-play-pause-key-to-launch-spotify-instead-of-itunes.1626645/#post-17779801" title="Can I assign F8 (the play/pause key) to launch Spotify instead of iTunes?">here</a>. But I didn't deeply try this option. There might be a little issue.
