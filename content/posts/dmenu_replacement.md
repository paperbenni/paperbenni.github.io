---
date: '2025-09-15T16:53:18+02:00'
draft: true
title: 'There is no replacement for dmenu'
showToc: true
---

# Are there really none?

We are now years into the transition to wayland, yet one problem still remains: 
There is no dmenu replacement. Instantmenu is based on dmenu, which remains
stuck on X11, which is becoming a problem. 
You might say 'look at fuzzel/rofi/whatevershinynewthing', but they are not what
dmenu was truly good at: Not interrupting my workflow. Instantmenu was truly
tiny. And the very first thing it did was to grab my keyboard input. 
I could make it part of my typing flow, as I could use it purely from muscle
memory without thinking about it. This is not possible with the wayland
equivalents of it. They all take a variable and non-negligible amount of time to
load. This means that if I continue typing before they loaded, the first few
keystrokes will go to whatever application is currently in focus. Depending on
what that application is, this could be annoying to disastrous. It also means
those characters are not in the menu when it eventually opens. Double bummer. 

# Why did nobody develop that?

Take the following with a grain of salt, I don't entirely know what I'm talking
about, but to me it seems plausible. I have considered writing my own wayland
compositor, so I've read a few things about wayland, but I have barely scratched
the surface, and it was enough to understand I don't have the time to do that. 

As far as I can tell, wayland is more complex than Xorg for the end user. I know
that Xorg was spaghetti, but it was spaghetti which was developed at a time when
hardware was limited, applications were more basic under the hood, and memory
and storage usage mattered. The end result when it worked was simpler to use
than wayland. Sue me. Wayland seems to be an ever moving target, people don't
like to just use it, and instead rely on fairly heavy libraries to abstract it
away. 

All of these libraries are meant for applications which you open and and then
use for a while. They're not meant for utilities following the unix philosophy,
they're large and okay with 80% feature overlap with some other thing and 40%
feature overlap with almost all other things. 


New approach:

```
- Server is running inside a terminal on the scratchpad, listens for menu requests
- on request:
    - show scratchpad
    - open menu prompt
    - wait for menu selection
    - close menu prompt
    - hide scratchpad
    - send back selection message
```




