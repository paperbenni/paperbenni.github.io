---
date: '2025-09-21T12:52:40+02:00'
draft: true
title: 'A new game save system'
showToc: true
---

# The problem

I do not trust many cloud save systems. Partially that's not their fault.

I am on Linux, so everything EpicGames is janky (even more than on Windows). 
Steam is pretty good, but even there, the cloud save system occasionally refuses
to sync. 

Regardless, I have spent a fair bit of time in some games, left them sitting for
a year, only to find out that something has swallowed my save file or that it's
on an old machine and has not synced over. 

I also like to play emulated games, or use tools like umu-launcher, so the save
file will not necessarily be in any folder steam expects or knows. 

I have tried Ludusavi, but it's very poorly documented, very slow, and partially
very janky. Apart from custom game paths, it also does really care about
emulated games. I also like to keep games self contained. Separate folder with
dependencies, wine prefix etc. Ludusavi doesn't really like that. 

# The solution

I do not believe I can build a better cloud save system than Steam or EpicGames.
I believe it has already been built, we just need to use it and build a friendly
user interface.

Restic has pretty much everything we need. It can detect changes for large
amounts of binary files, keep a deduplicated version history, upload to slow
cloud storage in an efficient manner, restore from that storage, guarantee
integrity, pull changes from the cloud, manage custom metadata, keep track of
different devices and more. 

# Ideas

Game saves as restic snapshots

`instant game sync <game>` command

For each game installation do the following:

- Check when the game save was last modified locally
- Check when the latest restic snapshot for the game was created
- If the game save is newer, create a restic snapshot for the game
- If the newest restic snapshot is newer, then restore the game save from the
snapshot

`instant game launch` command

`instant game init` command

prompt for restic repo to use and its password

# Research

Can I use restic to view
- are there any changes?
- what are the newest changes?
- are they newer than the newest snapshot?

# Features

`instant game add`

interactively prompt for
- game name
- path


# Architecture

All game saves are stored in a single restic repository.
Probably doesn't need a password, game saves are not that sensitive. 


## Files

List of games with universal metadata
`~/.config/instant/games/games.toml`

Device specific metadata, game can be installed or not, or installed in
different locations on different devices.
`~/.config/instant/games/installations.toml`

## Data
```

struct GameName(String)

Game {
    name: GameName,
    probable_paths: string[],
}

GameInstallation {
    game_name: GameName,
    save_path: string
}
```


A game save is a restic snapshot tagged with `instantgame/<gameid>`


## Wrappers

Either use Rustic as library or wrap restic CLI
- Restic more mature, probably use that


