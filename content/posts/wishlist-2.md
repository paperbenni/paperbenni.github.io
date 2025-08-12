---
date: '2025-02-09T13:26:28+01:00'
draft: true
title: 'Wishlist 2'
showToc: true
---

# Introduction

Time to make another software wishlist.
This time the wishlist has some smaller open-source software, and the features
are less obvious, but I would still very much like to have them.
Maybe I will even update this list if the features are added or if I get around
to adding them myself. 

# Neovim

Async Tree-sitter parsing in insert mode, or maybe pause Tree-sitter parsing in
insert entirely. Maybe revert to regex parsing in insert mode. It doesn't look
great, but I don't particularly care if I can avoid half a second of latency on
every keystroke. 

# Snacks.nvim

This is a plugin suite for Neovim which has a remarkable number of features with
remarkable quality. 

The file explorer should have the ability to choose the window in which to open
a new file. It is not entirely clear how the explorer chooses the window in
which to open a file, but coc and nvim-tree both have the same buffer picker. I
am not sure if this is from a plugin or if it is built in, regardless, I would
love the ability to use it with the snacks explorer. 

# mini.nvim

Another plugin suite, also very well done. 

## mini.files

This currently acts odd if you try to open Telescope or Snack picker. 
The picker appears for a second, but then both mini.files and the picker
disappear. Opening the picker again then works. Maybe mini.files should close
when pickers are open or find a way to stay open in the background.
I do not know if this is technically even possible, or if this is a neovim
issue, but it is annoying. 

## mini.pairs

Give me a keybind to jump outside of the pair. 
Give me the ability to disable the plugin in specific file types or buffers. 

# Yazi

Yazi solves all of the technical issues Ranger has. It is lacking the sheer
number of easily accessible features Ranger has, though. 





