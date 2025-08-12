---
date: '2024-12-15T12:26:22+01:00'
draft: true
title: 'Instantupdate'
showToc: true
---

# Intro

Instantupdate is a script that updates the system to the newest version.

# Ideas

incremental updates. Arch has a tendency to break when not updating for a long
time. Packages and operations are tested only so far as that they apply cleanly
to installations that are at maximum a few versions out of date. Installations
that are in a state that nobody has tested in months or years can break when
"skipping" intermediate updates. Keeping old update scripts around and executing
them one after another until the current version is the newest one solves this
problem, as the update script only gets executed on the version it was intended
for. 

# Issues

If the incremental update script relies on packages that don't exist anymore, it
will fail.  e.g. pamac-nosnap Replacing packages should maybe fail silently or
just remove old packages if the suiteable replacement is not found anymore. 

This issue is unsolved to date. Omarchy has a similar approach, but I also don't
see how it can solve the problem of intermediate states of the update process
being broken from the outside. 


