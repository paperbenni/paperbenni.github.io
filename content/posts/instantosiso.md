---
date: '2025-09-12T17:22:33+02:00'
draft: true
title: 'Instantosiso'
showToc: true
---

# Fixing the instantOS iso

The last instantOS iso was created a while back. I've learned a few things since
then, so here is my take on the updated plan to rework the instantOS iso build
system. 

Problems right now
- New iso build is mostly declarative to make it more reproducible
- Airootfs customize script was removed

Current plan
- copy releng config and make changes
- commit forked releng config to repo
Problems with that
- upstream updates difficult?
- Multiple sources of truth for dependencies

To solve this



