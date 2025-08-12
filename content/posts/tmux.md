---
date: '2025-08-12T16:11:46+02:00'
draft: true
title: 'Tmux'
showToc: true
---

# Less used tmux features

These are some tmux features which strangely enough I have not seen anyone use
like ever, because I believe everybody is too lazy to learn them, but still
spends more time with hacky workarounds than learning them. 


## Interactively close sessions

`Ctrl+B s` to open the session picker. Use vim keys or arrow keys to select the
session you want to kill. Press t to mark a session. You can mark multiple
sessions in one go. They will be marked with an asterisk `*`. Then press `X`
(Capital is important) to close them, and y to confirm. Done

The way I previously did this was to enter all the panes in the session I no
longer need, close all the processes until all of them are gone, and then attach
to the next session to repeat the process. The problem is, if you close the last
window in a session, you detach from it and tmux by default starts a new session
when you open it again. You can either manually attach to the next session or
open a bunch of empty shell sessions. Or just learn a few more hotkeys. 
I am writing this blogpost partially so I don't forget them. 

## TODO

### Copy paste

I have been using tmux for approaching 4 years now and I am still too lazy to
learn this. You can hold shift to use the terminal emulator to select and copy
text. The biiig problem with that is that if you have multiple panes, the split
characters as well as the other pane will be copied as well when selecting a
line. I mostly don't use tmux panes or use some other way like nvim or wl-copy. 
But that's dumb. I should either learn how to do this or write a script to do it
properly in case I don't like the tmux way. 

### Search

Searching through all sessions, including scrollback would be quite nice. 
Maybe there's a way to do that. I should look into that. 



