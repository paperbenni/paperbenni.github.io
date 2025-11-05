---
date: '2025-11-02T12:00:32+01:00'
draft: true
title: 'Winefilepicker'
showToc: true
---

Please improve the wine file picker. Unless I'm understanding something wrong,
the situation is the following:

When windows applications want the user to select a file, they can call a
windows API function which opens a file picker dialog, and the operating system
handles the rest. Windows opens a file picker dialog which is basically a
modified version of the windows file explorer. After the user selects a file or
cancels the dialog, the application receives the result (or a message that the
picker has been cancelled). 

Wine reimplements the Windows APIs for Linux which is how Windows
applications are able to run on Linux. The file picker for Wine is very basic
and incredibly lacking in features. It makes using any kind of productivity
software on wine a pain. If I'm running something other than a game through
wine, chances are not all the data which I need is within the wine prefix. It
might be in my home directory, or another drive. 
The wine file picker seems completely unaware it is running on Linux. For most
applications this is the goal, but in my opinion parts of wine itself should
work differently. 



Wishlist
- Recent directories
- Fast access to the home directory
- recursive search
- bookmarks
- display GTK file picker bookmarks
- Maaaaaybe a compatibility layer for the GTK picker?




