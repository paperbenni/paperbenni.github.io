---
date: '2025-08-12T19:40:11+02:00'
draft: true
title: 'The mouse is not stupid. Yes, I meant you, the nvim Hyprland Arch BTW user'
showToc: true
---

# Introduction

I am a heavy Vim user; I like to use keyboard-focused workflows whenever they
are available. I also have been developing my own window manager called
instantWM for a long time, and have tried all major window managers
and desktop environments, including macOS and Windows. 

Most Linux power users tout keyboard-focused
workflows as the end-all-be-all of interfacing with technology, and while I am
with them most of the way, I disagree with the "all" part. 


# When to use a mouse

While as software developers we certainly try not to use any software which
cannot be controlled through Vim keybindings, there are times where the best
tool for the job is one where the best way to use it is the mouse. 
The main advantage of not using the mouse is that your hands can stay on the
keyboard and do not constantly need to switch between the keyboard and mouse.
This becomes a rather inconvenient burden when you are using a tool where you
need the mouse. Most mouse-focused software has keybinds which can be used with
the left hand while the right hand stays with the mouse. The ideal state is to
stay that way, keep one hand on the keyboard, keep one hand on the mouse. 
If the window manager forces you to use the keyboard for everything, you will
end up constantly switching between mouse and keyboard, essentially doing
exactly what we were trying to avoid. Vim keys especially make extensive use of
the right hand, but so do arrow keys and countless others. 

The ideal window manager supports both states. It provides enough keybindings
to be usable without a mouse, but most features should also be accessible with a
mouse only. 

I also do not believe the number of people using a window manager who still need
to make extensive use of mouse-focused software to be small. Even if you are a
software developer or writer, you're doing it. Don't lie to me. The Chrome or
Firefox Debugger is better to use with a keyboard. There are tons of websites
which don't play nice with Vimium and even then, some are faster to use with a
mouse. Yes, you are using a web browser, again, don't lie to me!

If you're not a developer, you might use creative software which is inherently
mouse-focused. You are not navigating the Blender viewport or moving Figma
vertices with the keyboard. And if your work is something else entirely,
probably even more of it takes place in a web browser. 


# They're not mutually exclusive


I do not believe that keyboard and mouse-focused workflows necessarily have to
be mutually exclusive. There are exceptions to this. If your software makes
everything accessible via the keyboard, then GUI buttons take up unnecessary
screen space. There is a fundamental incompatibility between the approach Vim
takes and what Visual Studio does. You cannot give Vim the approachability of
Visual Studio (using that term very liberally here) without losing one of its
core strengths, that being the uncluttered appearance and ability to display a
lot of text at once. 

There are cases where this conflict doesn't exist though. The reverse of the Vim
case for example isn't true. If there is a GUI button for something, there is no
reason not to also add a keyboard shortcut which does the same thing as clicking
the button. (Well maybe the action is highly contextual, which makes
implementing keyboard shortcuts more difficult or impractical to use, but the
point still stands)

Desktop environments are a bit special in that regard because they are
inherently graphical. They do not need to plaster everything with buttons, but
they do need to display graphical windows and handle mouse input. I also have
yet to see someone completely omit some sort of status bar. These elements
are there; you cannot get rid of them. You do not gain anything by ignoring
mouse input events. If a status bar is there, then make it clickable. You can
still add keyboard shortcuts for anything the clickable areas do. Give them
different interactions if you right- or left-click on them. Make the status bar
do something if you scroll on it. Scroll to change volume, scroll to change
brightness, right click for more options. Scroll to switch workspaces. Hold
Shift or Super while using the mouse to interact with the bar to make even more
different actions quickly accessible. 





