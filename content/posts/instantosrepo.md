---
date: '2025-08-18T18:45:43+02:00'
draft: true
title: 'Instantosrepo'
showToc: true
---



I do not know why I decided to spread instantOS across tons of different repos. 
There is no value in having the different programs separate. The entirety of
instantOS scripts is under a couple megabytes. There is no reason anyone would
want to clone just a couple of them. Some of them depend on each other anyway. 

That is not to say all of the architecture is horrible. Dependencies don't go
both ways, most of them are to what is now in the instantutils package.

Even if I do want to keep them separate packages, there's still nothing gained
from having them in separate repos. 

Candidates for merging into one repo

- instantOS
- instantSETTINGS
- instantCONF
- instantPACMAN
- instantUPDATE
- instantNOTIFY
- instantTHEMES

Most instantOS programs depend on instantOS and instantCONF, so instantCONF and
instantOS merging is a no-brainer. And while we're at it, why not throw in
instantSETTINGS? There is virtually zero reason to not bundle them. You wouldn't
want either of them without the other. 
Most of instantTHEMES is probably going away. GTK theming is pretty much dead.
QT theming has always been a nightmare and still is. 
Pretty much all other applications can be themed using dotfiles, so I can make
the new dotfile management system do that. 
 should probably 

instantWM and instantMENU are also obvious candidates for keeping separate.
They're standalone programs. 

liveutils and iso

instantTOOLS should also stay separate. There are people who do not want or
should not want this installed. They're dev and debugging tools. 


dotfiles should probably stay in a separate repo to be easily handled with stow,
yadm, or whatever else I eventually decide to ship as a dotfile management
solution for instantOS. 



repos do be archived
- docker
- 32bit
- rox-filer
