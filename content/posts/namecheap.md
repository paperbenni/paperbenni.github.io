---
date: '2025-08-14T14:51:28+02:00'
draft: false
title: 'Namecheap is horrible'
showToc: true
---

# It's horrible

Stay away from it. They are not capable of delivering anything resembling good
service. 


# Horrible UI

The UI is terrible. 
There is a dropdown menu called "Actions" at the top which for years has only
contained a single action called "Delete". Why not replace that with a button
called "Delete"?

By default the entry management UI shows a whopping 5 entries.
There is a button which allows it to display all of them. 
So it's either 5 or potentially hundreds or thousands, depending on what you're using your
domain for. No paging. 

The functionality is different depending on your screen width. That's right, the
website is sort of responsive. But instead of reordering, and resizing the
components to fit the screen, they also arbitrarily add or remove functionality
when resizing the browser window. Some buttons or fields are hidden entirely
when you shrink your screen, some only appear on narrow screens. It's like they
let different teams create the different variants of their components. Or most
likely different interns who they fired years ago, as the web UI has not changed
in ages. 

The login screen is unable to remember my username. Probably missing metadata. 
The password manager does recognize the password field, but I need to retype the
username every single time. 

Their input validation is client side and also wrong. I tried setting up
stalwart, which is an email server which gives you a list of entries to put into
your DNS, and it refuses them, I override heir validation and it works just fine.

The notifications menu only appears upon hovering over the envelope icon in the
top right. It also disappears as soon as you move your cursor off the envelope
or the menu. The menu is also just a few pixels in width immediately below the
envelope, so if you move your mouse down to the menu it will disappear before
you reach it, unless you manage to travel over the tiny triangle connecting the
envelope to the menu. But make sure your computer is not too fast, because there
is a tiny gap between the envelope and the menu. If it is detected your cursor
is on that gap, then the menu will also disappear. So make sure your mouse
movement is precise, but also fast enough so that there is no frame where the
cursor is on the gap. 

Side note, all other menu entries in the navbar also have hover-over menus, but
do not have this problem. 

Everywhere I look there's low hanging fruit for problems to fix. 

Scrolling down to the footer makes the sidebar flicker and rapidly move up and
down. 

They use images for icons. Images as in a rasterized image format. 

The arrow in their breadcrumbs component is not aligned properly, and also too
small. 

Code blocks in their API docs have vertical misalignment and use multiple font
sizes within the same code block for some reason. Syntax highlighting on links
is also broken. 


# They think you're smart but stupid

Setting DNS records is hidden behind the "advanced settings" panel. This means
they assume their UI can be used by anyone who is not a power user or knows what
they are doing. The famous "casual DNS management user", a staple of all user
stories and persona testing meetings. Someone who is able to put up with all the
bugs in the UI, able to run their own website, but will get scared when
presented with a list of DNS records, and who also thinks the most important
feature which should be easily reachable is giving Namecheap more money. 



# It's lacking features

There is no way to bulk import entries from the WebUI. 
There is no way to export them either. 

# The API is horrible

It returns XML. Its documentation does not have a search feature. There is no
API Method to add a single entry. You have to override all entries every single
time. 


# Conclusion

I hope this was entertaining to read and loses them money (or gets them off
their asses to fix their shit, all of it is low hanging fruit and yet they can't
be bothered)


