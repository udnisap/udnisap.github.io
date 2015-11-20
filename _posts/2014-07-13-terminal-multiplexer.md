---
layout: post
section-type: post
title: Terminal Multiplexer
date: '2014-07-13T23:11:52+05:30'
tags:
- linux
- free
- productivity
- open source
- shell
tumblr_url: http://my-discoveries.tumblr.com/post/91706525570/terminal-multiplexer
---
I have been using screen for a while and wanted to use a newer tool as screen will not offer new features other than buf fixes. There were several alternatives. Terminator is useful if you are used to GUIs. But I needed it to be able to run on command line. So that I can use it on SSH sessions. I came across TMUX which can be considered as a predecessor of screen. Simply install with

apt-get install tmux

And you you can do all sorts of manipulations which were never possible on screen. TMUX has an abstraction of sessions, windows (more like tabs) and panes. Sessions can have multiple windows and a single window can be linked to multiple sessions. Panes are divisions of the window to run different shells. 
