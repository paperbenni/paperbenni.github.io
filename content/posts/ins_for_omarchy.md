---
date: '2025-10-02T15:04:27+02:00'
draft: true
title: 'Ins_for_omarchy'
showToc: true
---

# Introduction

Omarchy themes and its preconfiguration of your dotfiles are great, but they can be much much better. I came up with a new approach which makes three key improvements. I also created a command line tool which implements this approach. I initially developed it for instantOS, but the theming part of it can be used on any distro, and integrating this into omarchy should be pretty easy. It's available to try on the AUR and crates. 

```
Cargo install ins
````

# Improvement

## Improvement 1. More user freedom 

What if I find a theme, and I really like it. It makes my window manager, my GTK and notifications all really pretty. I want to use it. 
But there is a problem. I have some of my own configuration in ghostty, and I'd really like to keep it. There's my own shortcuts and my own font in there, and I like it that way and not any other way. You know, the Linux philosophy, I want it just the way I like it. 
The theme however contains a ghostty theme, so if I install the theme, my ghostty config will be overwritten. 
What are my options now?

- I can not use the theme. Kind of defeats the purpose of the theme
- I can backup my config file, install the theme and then overwrite some of the config files the the theme. But I will have to do this every time I update or change the theme 
- I can fork the theme and do my own modifications to it. Not ideal either as it comes with a maintenance burden

Turns out there is a better way:

`ins dot` allows you to have your cake and eat it too. If a dotfile gets modified by the user then that dotfile gets skipped when installing or applying themes in order to preserve the user customisations. All other dotfiles continue to get themed and updates as regular. Detection of user modifications is completely automatic and is ultra fast even with lots and lots of dotfiles. The algorithm is very robust, so detection of user edits works even when switching, updating, uninstalling or reinstalling themes. Even if you skip updates or roll back a theme, as long as the user didn't manually modify a file, it will get automatically updated just as the theme requests. 
Of course I can also explicitly discard my changes and reset my dotfiles to what the theme requests, and as soon as I do some of my own customisations, ins dot stops messing with the file to let you keep them

## Improvement 2. More comprehensive themes
 
What if I want to include a color scheme for an application which DHH doesn't know about? I'll have to request support for it, and then wait until that is actually implemented. Or even worse: the application is niche or proprietary, my request for support gets rejected. 
As the list of supported applications grows, so does the list of files in the theme folder. This requires coming up with an organizational scheme and waaaait a minute, we're reinventing the ~/. config folder. 
With instantdot you're just putting the files where they belong, just relative to the theme folder. 


## Improvement 3. Combine themes 

What if two different themes theme different applications?
I could install both and constantly switch between them, but that's kid of a hack. 

## Improvement 4. Easier theme development

The `ins` cli Tool Comes with helpers to develop and test themes. These don't
really do anything special, but they are super convenient and make the boring
parts of theme development a lot faster.

Let's say I am a theme developer and I want to add a kitty theme to my theme. 
The config file for kitty is `~/.config/kitty/kitty.conf`. I first play around
with the kitty colors to my heart's content, then I run `ins dot add
~/.config/kitty` to add the dotfile to my theme. It knows where to place the
dotfile, and in case it doesn't, it comes up with a menu asking which theme to add it to. 

I might then change my mind and do some further changes to the kitty config. 
My theme now already knows about the kitty dotfile, so I can run `ins dot diff
~/.config/kitty.conf` to see what I changed compared to what the theme contains. 
I can also run `ins dot fetch [file or directory]` and the tool will fetch all
updates to dotfiles contained in the theme to the theme. In the case of kitty,
if I am in `~/.config/kitty` this would just be `ins dot fetch .`

The `ins dot diff` and `ins dot fetch` commands work recursively, meaning I
could also run `ins dot fetch ~/.config` to fetch all updates to all dotfiles
contained within the theme. 




