---
date: '2024-12-13T00:23:08+01:00'
draft: false
title: 'Automated Dotfile Management'
showToc: true
---

## Introduction

instantOS relies on a lot of tools which use plaintext configuration in the home
directory and have pretty much all their features disabled by default. This
means that in order to ship a somewhat functional system out of the box, user
settings need to be managed in some automated way, unless the user modifies them manually.

In that case, automated changes in these files can be very destructive, as it
could lead to unexpected behaviors or loss of user customizations.

I aim to create a system that will not trip up users who do not know about it
and which will run quietly in the background.

## Imosid

My first attempt at automating dotfile management was the [imosid](https://github.com/instantos/imosid).
This project has somewhat ballooned to being way more work than anticipated, and
while a good opportunity to learn some Rust, it might ultimately not be a good
fit for automated dotfile management.

The idea behind imosid is to divide the config file into sections, and then
compute a hash for each section. If the section changes, then the hash will no
longer match its contents and the section will stop receiving updates.

A user should not have to know about imosid or have to pay attention to it.
Section syntax can be broken or invalid, and imosid will just quietly mark the
section as modified and move on to update sections which are still valid and
unmodified.

The section approach has a few problems. There can be no dependency between
sections. If a section references another section, then updates to the first
section may break the second section.

The naive solution to this problem is that anything that any dependencies of a
section should be part of that section. This means sections can grow quite big,
which diminishes the usefulness of the system.

Even if there are lots of small sections, if a user does not know about
imosid, they could easily add parts to the config file which depend on
unmodified sections. If the unmodified section gets an update, the user written
config may still break. The same goes for duplicate keys. If a section is
updated by imosid to have a key that is already present in the user config, the
user config will also break.

Unexpected dotfile breakage to the casual user just looks like the system
spontaneously going haywire.


It also leaves a bunch of ugly comments with section markers and hashes in the
file, and for file formats that don't support comments, there has to be a second
metadata file to keep track of the hashes.

## Yadm

Yadm is basically just a git wrapper. It tracks the entire home directory as a
git repository, but defaults to ignoring every file except for files explicitly
added. The fact that the home directory is the working directory means that
dotfiles can be edited directly in their intended locations and never get
overwritten by third party tools.

Of course, git seldom fails quietly. Yadm doesn't have a built-in way to be used
non-interactively. If a user modifies a dotfile that is tracked by yadm, yadm
(being git) will just refuse to do anything until the user commits the change or
gets rid of it.

I do not want my terminal colors to stop updating just because I changed my
bashrc, so my goal now is to create a system that will update dotfiles via yadm,
but stops updating a dotfile as soon as it diverges from the yadm version.

## Pacdiff

As a little side note, the way Arch handles dotfile updates also has a few
problems, namely that it requires user interaction at every point.

Root-owned config files are included inside pacman packages, but at the same
time are meant to be edited by the user. This means that when updating a package
which contains a new version of a config file, the file does not overwrite the
current version, but instead gets saved as a pacnew file. Arch does not know if
the current version of the file is different from the pacnew because the user
has done modifications which should not be overwritten, or if it is simply from
an older version of the package. In the latter case it should not be a problem to
simply overwrite the file. It might in fact be a good idea to overwrite the
file, since new versions of the package might require a different format of the
config file.

This means the user is required to review the differences between the current
and new version of the file and can then merge them manually. It might be
convenient to use an automated merge tool for this, but if a file has been left
unchanged by the user, and some settings have been removed from the new version,
then the version an automated merge tool will produce will have old unused keys
next to the new keys.

There are plenty of users of Arch-based distros who do not know about this and
just end up using really old version of config files with newer versions of the
program they configure.

I do not know what the best solution to this problem is, but the way it is
currently implemented in Arch is not ideal.

## Why not stow

stow symlinks files from a git repo to a directory in the home directory. This
means users editing the files will directly edit them in the git repo and we're
back to having problems with updates. 
That said, if stow offered the ability to ignore files already existing, this
could work. 

Updating could work like this:

- Go to the git repo
- List all files with changes
- For all of these, remove the symlink, copy the actual file to the target
destination
- Checkout the files in the git repo to restore them to a clean state. 
- Run stow again to create any new symlinks

TODO: Look up
- What happens in stow if a file already exists?
- What happens if a symlink already exists? Can we override it?
EDIT: it can't, stow is not viable

Side note, files can easily be reset by deleting them and running stow again

If symlinks can easily be overwritten, then themes, community plugins etc. are
all possible. 

We do lose access to template like things like yadm, but maybe that can be
reintroduced. Maybe even with more widely used templating languages. 


## Automated yadm?

Maybe yadm can be automated, this document will contain some ideas on how to do
that.


### Merge recursive ours

This is relatively simple to implement, just automatically pull upstream changes
and merge with the `--ours` strategy. This will preserve user changes wherever
there is a conflict. The problem is that if there are no conflicts, this can
still result in unexpected behaviors. If a user modifies a section of a dotfile
that hasn't been changed upstream and upstream updates another section, the
resulting dotfile will have both the user changes and the upstream changes.
If both upstream and user have added the same key but in different locations,
this will result in an invalid dotfile.

### Custom merge driver

Maybe I am just stupid, but I cannot find a built in way to guarantee a merge
results in only files that have existed in that exact state in some branch.

Time to dig into git features where the amount of good tutorials and examples is
single digits.

Merge drivers are programs which merge individual files if they have diverged
between the two branches being merged. They can be implemented by custom
programs which are then called by git when configured to do so.

Git can pass arbitrary data from the merge process to the driver as arguments.
In our case we pass the following arguments:

- `base` is the last version of the file that is identical in both branches
- `local` is the version of the file that is in the current branch
- `remote` is the version of the file that is in the other branch
- `output` is the file to write the result to

If there are local changes, use the `local` version, otherwise use the `remote`
version.

## Dumb git script

This is purely for brainstorming, not meant to be comprehensible to anyone but
me. 

Clone yadm repo

update:

fetch
get list of modified files, create automated commit
name scheme
- date
- auto marker
remember hash
merge upstream
get list of merge conflicts
for each conflict do git checkout file from last auto commit
add all conflict files
automated commit 2

ideas for implementation
maybe don't use yadm at all
TODO for looking up
- git worktrees
- how does yadm work
- ignore all by default? How does yadm do that?
- use bash?
- use libgit2?




