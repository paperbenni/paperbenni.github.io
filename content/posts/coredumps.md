---
date: '2025-11-18T22:22:23+01:00'
draft: true
title: 'The most insane default I have ever seen'
showToc: true
---

# This is the most insane default setting I have ever seen

I have no idea how not more people are talking about this. 

Whenever a program crashes, systemd will take a core dump and save it to disk.
As far as I understand a coredump contains the entire memory of the crashed
program, RAM, cpu registers and everything. In most cases, the programs which
crash in a way which produces core dumps are quite large, complex and deal with
large amounts of data. For me this has been modern games and electron apps.
Because of the memory consumption of these programs, and because I have 32GB of
RAM, the core dumps produced are often tens of gigabytes in size. 

Google's Antigravity managed to create a background crash loop or
crash a bunch of different programs, which resulted in 60GB of core dumps
being written within minutes. 

Yes, antigravity is a horrible piece of vibecoded shit, whose only justification
for existence is free access to Gemini 3, although even that is rate limited to
hell and incredibly buggy. 

But the OS shouldn't make it 100 times worse. 

This is absolutely horrible for several reasons: Given that I had 70GB of free
disk space, this was dangerously close to filling up my entire disk, and I had
to reboot before it reached 100% disk usage. 

Producing a coredump completely maxes out the disk IO, making the system very
unresponsive. 

In the case of Antigravity it was hard to kill the
program because I didn't have pkill or btm in memory, and reading them from disk
took ages. Even if you have a really fast SSD (which mine should be, it's a
relatively recent NVME drive), things will slow to a crawl. 

Who uses core dumps? What is the target audience for this feature? I am fairly
certain that the majority of coredumps produced are never looked at or even
noticed, apart from their destructive effects. 

Can you really argue that the majority of users use this feature? Even if you
take it as a given that the user is a developer, most users are not the
developers of the programs which tend to crash, and these programs might not
even be open source. I am a software developer, but when a program crashes, I
grumble, restart it and maybe try to avoid the conditions which made it crash. I
don't go digging through core dumps, trying to decipher what went wrong. Even if
I do decide to do that (provided the program crashes often enough for that to be
worth it), there are tons of places where I go before I decipher its memory.
Logs, systemd journal, a debugger. Which brings me to the developers of the
crashing programs. I don't think even they use core dumps that often. They too
will probably use logs and debuggers first. And if the program is written in an
interpreted language, then the developers might not even know what a coredump
is. Node and Electron have both managed to produce gianormous coredumps for me,
and yes, it probably shouldn't be possible to write JavaScript which gets these
to segfault, but if it does happen, then I WILL NOT TRY TO DECIPHER THE MEMORY
OF FUCKING CHROMIUM. I might send the problematic JavaScript to the
Node/Electron/Chromium developers, and hopefully they can reproduce and fix it,
but are you honestly telling me that the average user wants to, let alone is
able to wade through gigabytes of memory dumps because they want to fix their
JavaScript code? Or because their unfinished buggy AAAA Game crashed?

If you knwo what core dumps are and are capable of using them, then you are
probably also able to enable them, but for the majority of users and use cases,
they should be disabled by default.


