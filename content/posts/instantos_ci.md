---
date: '2025-10-31T14:01:37+01:00'
draft: true
title: 'Instantos_ci'
showToc: true
---

# A CI system for instantOS

The way packages are built as of now is very adhoc and means fixing issues with
packages and rebuilding them takes a long time. 

# The current process

## How it works

1. Build packages on my local machine
2. Rebuild packages database
3. Sync the entire folder to the web server using ansible

## Problems

### Not very reproducible

My dev machine is a machine I regularly mess with. It won't have malware on it,
but maybe some env variables or troubleshooting steps impact the way packages
are built. This means if my personal machine is in an odd state, I cannot build
new packages, because I do not want to push messy stuff to my users. 

Similarly, if something builds *because* of something I only have on my dev
machine that's bad as well. It's not like I would know because so far my dev
machine has not broken down, but in case it does, it wouldn't be nice to find
out instantOS relied on something that died with it. 

### Not signed

The packages are not signed as of now. I want to create an instantos-keyring
package and sign packages. 

### Always updating the whole repo

Partial updates are hard using this approach. Because ansible always uploads the
entire repo, I need to make sure all packages, even the ones I did not rebuild
are present and valid and up to date. I usually am not sure, so I just rebuild
the entire thing. This can take quite a while, and after leaving the machine for
a while I still need to remember to run ansible to upload the changes. This also
means that I need to plan ahead each time I update a package. 

# The new process

## What should it provide?

I want to update packages through Git. I want to create a release with a tag,
and it then should build the package, sign the package, rebuild the database and
upload the package to the web server. 

I also want to provide some AUR packages prebuilt. Adding and removing them
should be as easy as adding the name of an AUR package to a list in a repo.

I should be able to have programs in individual repos, but also be able to build
multiple packages from a single repo. 

Atomic updates. While updating or rebuilding or uploading, installing or
updating instantOS should not be broken. 

## Brainstorming

![architecture](/posts/images/build_arch.svg)

Build in DIND archlinux docker image

How to get onto web server?
When to rebuild database?
Sign packages?






