---
date: '2025-02-10T13:33:25+01:00'
draft: true
title: 'Immich'
showToc: true
---

# My thoughts on Immich


Immich is amazing. It looks like Google Photos, it feels like Google Photos, and
it's even faster. Google Photos tends to move infrequently Photos to really slow
storage, so going through your timeline can be very slow. 
The desktop version of immich is also worlds above whatever Google cannot manage
to achieve. Video playback works without tons of buffering and dealing with what
seems to be an outdated and probably unmaintained fork of the YouTube player. 

I really wish it were stable though. The project is several years old now, has
lots of users, developers and funding, so this is definitely a possibility.

I really really cannot use it for more than occasinally playing around with it.
Every time I do, I really enjoy myself until I get to some huge problem which
means I cannot use it to replace Nextcloud or Google Photos.

During the last update, somehow the password of the database user was changed. I
did not update the database, just the immich server. 
The database in the recommended docker compose file is tagged with a hash, which
is usually not a sign that it is a recommended or stable version, so it might
have been a bug in the database, or the server has permission and shomehow need
to change or delete the password. I manually changed the password back using the
psql cli inside the database container, and not everything is working again. 
Running imperative commands on a database with docker where everything supposed
to be declarative feels pretty dirty, and the fact that the DB can still get
messed up is scary enough for immich not to be a good backup solution yet.

The backup UI on the mobile app is either very unclear or very buggy. 
I am not a fan of the header "Uploading file info". It sounds like it's just
uploading metadata, when it is actually uploading the file.

The remainder count frequently shows 0, even though there are still photos and
videos currently uploading. The total and backup counters are a bit unclear as
well. Does Total refer to the total number of files for my account, or the total
number of photos on my device, regardless of how many have been backed up?
Or maybe it counts all automatically uploaded files, not including files that
were uploaded manually or from other devices?

What does the Backup counter mean then? How many files are on my account? Why is
it higher than the Total counter?

The progress bar for uploading files is very unclear as well. Right now I am
looking at my phone, and the bar is stuck at 100% for a file. I am unsure if the
file is uploaded already, or if it is at least being counted as uploaded. The
"Start Backup" button is still there, so it might not be doing anything. Tapping
the "Start Backup button" turns it into a "Cancel" button, after which the 100%
bar does not change, and nothing appears to be happening. There is no indication
that there are not any files to upload either. It might even be better to show
the amount of files which will be uploaded before starting the backup, or
disable the "Start Backup" button if there are no files to upload.

I am not saying the immich developers are incompetent, or that this is the most
horrible UI out there, but it does not make me trust it enough to use it for
backing up my photos. The backup process is absolutely critical for a photo app.
I can deal with occasional jank when viewing photos, as long as I can trust that
the photos are actually there. 


