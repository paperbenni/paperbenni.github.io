---
date: '2026-02-06T16:10:42+01:00'
draft: true
title: 'Kilo CLI followup'
showToc: true
---

# A surprise to be sure

I disliked the old CLI, and as it turns out so did the developers behind it, and
they replaced it with an OpenCode fork. I like OpenCode, so from a user
perspective this is an upgrade. 

This article outlines issues I still have, and a wishlist of features. I will
lay out my case for why these should be implemented and why I think they're
doable. 

# I want Termux support

## Coding on mobile

AI coding agents have made coding on mobile viable Typing speed is no longer the
bottleneck, even less so than it was before. Termux is no longer a toy now. 

Cheap AIs like GLM 4.7 or MiniMax M2.1 can very much replicate traditional
coding workflows by doing the typing for you. You can absolutely write ugly,
typo ridden pseudocode on a small keyboard and get usable results out the other
end. 

Furthermore, models like Codex-xhigh like to think for hours at a time even on
short prompts, so writing those on a phone and checking in every hour or so if
the model needs further input is a reasonable workflow. 

## Please do it

OpenCode does not run on Termux without significant hassle and breaking other
things in the process. 

This is mainly because of two issues as far as I can tell:

Bun does not run on Termux as of now. 
Whatever binaries OpenCode contains are not compiled for stock Termux. 

Termux is run by volunteers and until now nobody has bothered to package bun for
it. Given that deno and node both run on Termux, this should just be a matter of
putting in the same work for Bun. It's just that nobody has done that yet
because it'll probably take a day or two, and Termux is mostly unpaid
volunteers who don't find messing with compiler settings fun. 

Bun on Termux would in general be great, I miss it dearly whenever I deal with
anything JavaScript on my phone. 



# Termux support

Claude code works well on mobile through npm
Claude code is breaking npm support, 'native' version does not work on Termux


# Put kilo in the Zed ACP registry

I want kilo in the ACP registry for Zed


# Some UX gripes

Slash commands do not show keyboard hints, ctrl p menu does though Is kilo
web/desktop a thing? `kilo web` does work, but the web interface is still
entirely the opencode branding


# Are we getting Kilo-Web/Desktop?

I want the web version to keep being a thing (not just tauri/electron)
I dislike using web-based tech because there's always a certain jank to it that
isn't there with good (emphasis on good) TUIs. The feeling of typing in neovim
is just different than with VS Code with the neovim plugin. The terminal
emulator just needs to do font rendering, nothing else. And it does a better job
at it than Chromium. I'm sorry, that's just the case. 
Compared to a browser, a terminal emulator is trivial. It really does not do a
lot. Kitty and Ghostty still spend insane amounts of time on optimizing the few
things a terminal emulator does and it shows. 


Lazygit/delta
neovim





