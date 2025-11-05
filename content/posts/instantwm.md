---
date: '2025-08-12T16:34:29+02:00'
draft: false
title: 'The Future of instantWM'
showToc: true
---



# The state of Wayland

I started instantWM in (I believe around) 2019. 
Wayland adoption was low. It had major open issues. Screen recording. Screen
sharing. No support from Nvidia. No distros using it by default.
No software ecosystem with utilities coming even close to what Xorg had.

Some of these are still issues. Flameshot does not work by default on Wayland.
It still complains after applying a few fixes. 
Espanso is really hacky on Wayland. Some features straight up do not work.

Some things about it are broken by design, features that will never make it in
there, but which some applications rely upon. These applications will stay on
X11 and be partially broken when running in XWayland.

There still is no proper replacement for arandr. Nothing compositor-agnostic
anyway.

But it is becoming clear that Wayland is where Linux is headed; there will come a
time when new applications will be developed without X11 support, or when
existing applications will drop X11 support. Wayland compositors will have access
to old applications via XWayland; X11 window managers will not have access to newer
applications. For that reason, as flawed as Wayland is, I believe the best
course of action is to prepare switching to it. 

I have been porting lots of instantOS utilities to Wayland, and have been using
Sway, Hyprland, and Niri for a while now.

Wayland is stable enough to make it the default on instantOS now. 



# Features unique to instantWM

instantWM has features I have not found in any other window manager or desktop
environment and which I miss dearly since switching to Wayland.

As the years have gone by, my belief that these are unique, and better than any
other solution out there has strengthened. 
I do not believe I am a better UX designer than what Big Tech or the Gnome
project has to offer, just that none of them are prioritizing features which
work well and fast over anything else. And I don't blame them for that, they all
want to strike a balance between their software being easy to learn, easy to use
and to actually do its job. 

instantWM is confusing at first, and I am never going to change a feature to
behave in a way I deem to be worse, just so that the first 10 minutes with it
are more pleasant. That means that to me personally it is faster and more easy
to use than anything else I have tried so far, and I believe that for anyone
willing to spend the time to learn it, it can be as well. And I do not even
think that instantWM is particularly hard to learn or that it takes a long time. 

A good example of this approach is resizing windows. GNOME and all traditional
desktop environments place small hitboxes around a window that when clicked and
dragged start the resizing process. Hyprland does not have these and instead
requires you to hold down a key on your keyboard, and the entire window becomes
the hitbox for resizing. 

instantWM supports the Hyprland approach of resizing a window, but also a mouse-
based approach that to my knowledge is unique. There is no hitbox around a
window by default. Anything behind the window stays interactive. The problem,
the hitbox approach faces that if the hitbox is very small, then it takes longer
to move the mouse onto it, because you need to slow down or move it back if you
overshoot. If you make it too big, then you can accidentally trigger it while
trying to interact with something behind or next to the window. 

instantWM has dynamic hitboxes. When moving the cursor onto a window, the window
then gains a fairly large hitbox around it. Clicking that hitbox results in the
resizing process being started. Right clicking allows moving the window (not
just at the top). If you leave the hitbox by moving the cursor outside it and
its window, then it disappears until the window is reactivated. This allows
windows to be moved and resized purely using a mouse, while at the same time not
impacting keyboard-based workflows at all. It is faster than the 'tiny permanent
hitbox' approach, because the hitboxes are a lot bigger. I can move the mouse
onto a window very quickly, and I can also move it next to a window very
quickly. (In most cases the window we want to resize or move is the one we are
currently using anyway). I do not have to aim for a narrow area where the window
border is interactive. 

Most of its features are also accessible with the mouse, without sacrificing the
viability of the keyboard focussed workflow, which remains its primary focus.
Besides resizing, you can drag a window to the top to deactivate the floating
mode, you can drag a tiled window from the top to make it floating. You can drag
a window to a different tag (= workspace). You can open an application launcher
by clicking on the desktop. You can open the menu by clicking on a button in the
top bar. 

Especially the interaction between the status bar and a Wayland compositor tends
to be really basic in comparison. 

# Options going forward

## Libraries

Ideally there would be a library which comes close to the level of abstraction
XLib offered. I want high-level functions which place windows in certain places,
focus them, hide, show or close them. I want surfaces to draw text on, and an
event loop which receives keyboard and mouse input events. I do not want to be
concerned with rendering or things like screen capture or XWayland support. X11
had its problems, but the high level developer experience was nice. The Xorg
server handled the chaos. The window manager did just that, it told windows
where to go. And if I don't have issues with how existing solutions do
rendering, then I don't see why I should implement them myself. I can see the
value in a monolithic wayland compositor, but it does tend to lead to less
commonalities between different compositors and makes them more time consuming
to develop, something I quite frankly do not have the time to do. 

### WlRoots

This is the library most Wayland compositors (besides GNOME and KDE) are based
on. It seems the closest to what I want from an Xlib alternative. 
I wanted to use Rust though and wlroots doesn't have great support for that. 
It also seems to have very spotty Nvidia support. I recognize that Nvidia is to
blame, but it's still nice that the others do a better job at putting up with
Nvidia's bullshit. 

### Smithay

This is a Rust library for creating Wayland compositors. Niri is really solid,
and with Cosmic also being based on it, it certainly enjoys a lot of support. It
is a tad bit too low-level for me though. Things like XWayland support are not
there out of the box, and I fear I will have to debug a lot of application
specific issues because the instantWM rewrite would necessarily be different
from other compositors. 


### Hyprland

This has gotten quite popular over the last few years. It looks nice and seems
well supported. DHH also started a product called
[Omarchy](https://omarchy.org/) focussed around it which seems really similar to
instantOS in idea and execution. 
The important part is that Hyprland has a plugin system which allows access to
pretty much all it has to offer and allows for quite massive changes to its
behavior. From what I've seen, it does
There are a few drawbacks. I am not very familiar with C++ and will not be able
to use Rust for this. Seeing as the project gets smaller in size by having
access to what Hyprland can already do, putting up with C++ is not a big deal.
Hyprland also has animations which are way better than what instantWM ever had. 
Dragging windows within a tiled layout is also really nice. 
Given how much the plugin system allows I feel confident that I will be able to
replicate the features which were unique to instantWM while also decreasing the
maintenance burden. 

The other drawback is that the Hyprland developer is currently banned from
freedesktop, and regardless of what went down, relying on a project which has an
adversarial relationship with the biggest organization in the world of Linux
desktop development sounds a bit worrisome. That said, this incident seemed to
only involve the Hyprland founder and an individual person within freedesktop
who had a disagreement over a badly moderated Discord server with offensive
jokes and an asshole moderator in it. The project at large does not seem
involved in tons of drama, and if the developer is a transphobic lunatic, he at
least doesn't talk about it. Hyprland is at this point developed by multiple
people and big enough to be a target for application developers or at least big
enough for people to fix enough issues so that most software runs on it. 


