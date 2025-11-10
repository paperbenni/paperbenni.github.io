---
date: '2025-11-10T12:23:57+01:00'
draft: true
title: 'Modernizing instantASSIST'
showToc: true
---

# Modernizing instantASSIST

instantASSIST is probably my most used instantOS utility. It provides emacs-like
keyboard shortcut sequences (chorded keybindings) for doing a variety of tasks for which I do not want
to interrupt what I am doing. There is one problem with it though: instantMENU
is stuck on X11. These days Wayland is less and less optional, and that makes
using any X11 software for latency critical tasks a problem. You can read more
about that [here](/posts/dmenu_replacement).

# Sway

Sway has a really nice feature called 'modes'. By default it is used for
resizing windows using the keyboard. When entering a mode, the entire set of
keybinds is swapped with something else, which is perfect for chord keybinds
without latency, as we are not starting a new application to enter a mode. 

The idea of getting instantASSIST to work better on Sway is to automatically
generate Sway modes for instantASSIST key chords. 

`ins assist activate sway`

`ins assist run <keychord>` calls are then mapped to the different hotkey modes

## Open issue

- introduce modes via swaymsg?
- do I need to modify the sway config?
- Can I source sway config files using swaymsg?
- How do I display the available options?

# Hyprland

This will use `ins menu`

# Others

Will use `ins menu`, which also needs a fallback for platforms which do not
support scratchpads. 


# Architecture

The data sctructures for definining different assists in instantASSIST should be
serializable to a Sway config file, which can be included into the main config. 

I should come up with maybe a builder pattern or a registry for creating new
assists. In a similar way to how `ins settings` entries work, there can be
requirements registerd, which need to be met in order for the assist to be
executed. 

