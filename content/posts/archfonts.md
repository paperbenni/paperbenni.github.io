---
date: '2025-09-10T19:30:58+02:00'
draft: true
title: 'Font Incident on Arch'
showToc: true
---

# Font incident

I have had a pretty good experience with Arch Linux over the years. 
I know people say it's scary, beta and unstable, but I've always seen this as a
bit overblown. Every program packaged for Arch Linux is the current stable
version or maybe even behind the latest one. They're not compiling
experimental stuff from not-yet-merged PRs. OR SO I THOUGHT. WHAT THE HELL
HAPPENED TODAY?! (Wed Sep 10 07:42:08 PM CEST 2025)

I was working on my laptop, checked for updates and found just a few packages. 
Nothing scary, no kernel modules, and besides, I'm not using proprietary drivers
or custom kernel modules or any of the other things which tend to break, so I
just ran the update in the background and forgot about it. 

Until I opened Sublime Merge which immediately froze.
I didn't think much of it, it's a proprietary program from the AUR, who knows,
it's a bad habit to use it at all. 

Went back to lazygit and everything was fine. Until I opened another kitty
instance. It froze immediately, cursor half drawn. 

Opened foot, which did not freeze, started kitty from there, still frozen.
Nothing about that in the logs, no error, nothing. Same story for ghostty. 
I reset my zsh config, and voila, kitty worked again. 
Okay, maybe there's some invalid unicode in my prompt, but even then it'd have
to be really bad to freeze kitty instead of rendering as missing characters.
I commented out different parts of the config until I landed on starship.
Starship definitely does not output invalid unicode, it does however use Nerd
fonts. Okay, maybe an invalid nerd font was installed. Uninstall all fonts from
the AUR and all the lesser used ones, reboot, rebuild font cache, reboot again,
same issue. 

Eventually I found out that seemingly random characters made seemingly random
programs freeze. Does not have to be nerd fonts or anything weird, can be a dash
or a dollar sign. Firefox is mostly fine with some minor issues, but Chrome has no issues, Sublime Merge is an
instant crash, Kitty is fine if you do not render nerd fonts, ghostty crashes
entirely, waybar is invisible, gnome-font-viewer does not start, nautilus
however is fine. 

After Googling around, I find out that the only thing most of these have in common
is FreeType. The issue seemed to be that some font rendering calls entered into
an infinite loop.

I don't think asynchronous font rendering is a thing, so all programs
encountering one of the characters which shall not be rendered froze. 

But surely freetype couldn't be it? Surely when updating a library which pretty
much all GUI programs use, somebody booted it up on a desktop and checked if
the basics are working before pushing out the update?

About an hour into a frantic troubleshooting session, I checked for updates
again, and found two updates: freetype2 and the 32 bit version of it. 

I install them, and all the problems are gone. All of them. 

HOW?? WHY??


