---
date: '2026-06-25T18:27:40+02:00'
draft: true
title: 'Herdr review and wishlist'
showToc: true
---


# I love it

It's tmux but without the bullshit. Tmux by default makes nvim look weird. It
needs manual configuration to have proper mouse support. It does not reattach to
sessions by default. It makes selecting things in the terminal a pain, and it
makes copying to the system clipboard over ssh a pain. Its default theme looks
terrible. Its catppuccin theme needs you to install a bunch of bash files and is
not easily committed to dotfile managers. 



# Herdr wishlist


## Search within selection mode

Searching the scrollback buffer is something most terminal emulators do very
poorly in comparison to proper editors. No regex, no history of search terms, no
copying resulting lines to the clipboard without selecting with the mouse what
the search already highlighted. Given that terminal users in particular tend to
dislike using the mouse, I find the reliance on it strange. 
Tmux has a vim like mode, which is an improvement, but kind of bad in execution.
Keybindings in particular are very strange. Why is copy not 'y'? Who are you
appealing to? It's in an uncanney valley of sort, giving vim users the feeling
of familiarity, but constantly feeling like something is wrong. 


## Block selection

Copying things out of a TUI is often times very annoying. Selecting an antire
line means including decorative UI elements or other content which happens to be
next to what you want to copy. Vim has a very nice way of dealing with this:
Block selections. You select two points and the selection becomes a rectangle
with those two points at the diagonal ends. I really dearly miss that whenever I
copy things out of lazygit (includes commit lines or branch names, a coding
agent (includes ui and status info), neovim (includes line numbers), and
basically any other TUI you can think of. Some TUIs remedy this by introducing
their own selection logic, which does help, but those mostly do not allow
selection via keyboard or search, and a lot of TUIs simply dont have it. 



## Port forwarding

Herdr is aware of the agents running on a remote server, and selecting text will
copy remote text to the local clipboard. It is in many ways a way to move your
dev workloads off of your local machine. Moving them off the local laptop means
there is a need for a way to see what's happening on the remote machine. Most
agent development is Web and CLI or API applications (as that is what agents can
interact with themselves), native desktop apps tend to fall apart much easier.
With remote herdr, while the agent can interact with the applications just fine,
the user cannot. It'd be nice if just like herdr is aware of agents running in
panes, it could also be aware of things like next js or vite dev (or other) dev
servers running in panes. Detection of these could probably work in a similar
way to how agents and their state is detected. 


## File transfers/mounting

SFTP exists, and works through ssh, herdr is an ssh client which has some
awareness of what is happening within it. (and also has a server it can talk to
on the remote host). It would be awesome if files could be transferred between
my client and the remote machine, maybe even FUSE mounted. 
I like how herdr does not reinvent the wheel in terms of agent UIs and instead
just integrates with their existing TUIs. Maybe this could work in a similar
fashion through integrating with yazi (which has an excellent lua integration. I
have created a nice file picker by writing a custom lua config file to a tmp dir
and launching yazi with that config file)


## Previews in pane switcher menu

This is one thing tmux does remarkably well, its switcher (`prefix + s`) takes
the full screen, and the bottom half shows a preview of what you are about to
switch to. This means I can open it and just hammer my arrow keys to get a great
overview of all that is happening. The herdr switcher shows names only, and
still manages to be quite crowded. 

## Reusing SSH connections

`herdr --remove something` opens several ssh connections as part of some
hanshake before establishing the connection. This is slightly annoying because
connecting takes about 5 times longer than simply `ssh something`. If you
connect without an ssh agent, herdr will ask you for your password several
times, which means it does not reuse the first ssh connection it makes, it
closes it and opens a completely new one, not even persising the credentials. 
Herdr does not do anything revolutionary, it's just more convenient than tmux,
and in this case it clearly is not, typing my long ssh key password 4 times on
my phone just to quickly check something is a huge UX papercut. 

# Please do it

I know many LLM focussed



