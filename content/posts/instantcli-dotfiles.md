---
date: '2025-09-06T20:50:00Z'
draft: true
title: 'Instantcli Dotfiles'
showToc: true
---

# Idea

I want to unify lots of things into an instantCLI
the base command will just be `instant`

# Dotfiles

I wrote about ideas for dotfile management a while back. 
I thought about it some more. I am abandoning the "home dir as git worktree"
approach. It's just not flexible enough.

What follows is incomprehensible pseudocode for the new solution

# Overlaying repos

Dotfiles can come from multiple repos. 
Those repos have an order. If a dotfile exists in multiple repos, the
version from the one with higher priority gets used. 
This allows for easy application of themes. 
It is not specified, which applications a theme can theme, and multiple
themes can be used and removed very easily

# Leaving the user alone

instantOS should remain hackable without bothering users who do not want to
learn its tools. This means user configurations should not be overridden, ever.
The tool will keep a list of valid hashes for a file, and if a file doesn't
match any of them, it is assumed to be modified by the user or another program
and will be left alone. 

# resetting files

If a modified file is markwd as valid, it will automatically be reset
to the latest official version on the next update



