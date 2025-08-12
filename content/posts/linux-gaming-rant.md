---
date: '2024-12-30T11:10:52+01:00'
draft: false
title: 'Linux Gaming Rant'
showToc: true
---

# Disclaimer

This is a script for a video I started writing a few years ago. 
I didn't want to see it rot in a notes app I no longer use, so here it is. 
I may have formulated it differently nowadays, but the point still stands. 

# Rant

I have long been using Linux as my primary operating system for gaming. Back
when I couldn't get wine applications to access the internet I never ever would
have thought that the majority of AAA games would ever run on Linux. I love the
platform and am amazed at how far it has come. However, there are things that
don't work on Linux. And oftentimes the fault lies not with Linux developers.
However, this does not change the fact that some things still don't work, and
problems don't get better if nobody talks about them. Lately I have increasingly
come upon people on Linux communities who seem to function along the following
lines:

Step 1: Come upon a statement. 

Step 2: "I wouldn't like it if this were true, but I'm too lazy to look up if it
is true, so I'm going to assume it's false"

Step 3: Mercilessly attack anyone who makes the statement with the most
braindead arguments you can think of. 

Alternatively: "I know what I'm saying is wrong, but as long as I don't like
someone, anything said against them is justified"

A good example is EasyAntiCheat in Proton. On Windows EasyAntiCheat works on the
kernel level. Wine works only in user space, it cannot access the kernel level. 

https://en.wikipedia.org/wiki/Wine_(software)#Basic_architecture

This means that the design of wine is fundamentally incompatible with the full
current version of EasyAntiCheat, and any version running on Linux has the
kernel level features disabled. 

Assuming that the kernel-level features do anything at all besides stealing data
means that by disabling them you will make cheating slightly easier. 

Here's where the behavior mentioned earlier kicks in: Deny this fact, claim the
people stating it are wrong or lying, and assign bad intentions to any game dev
who wants to simply remove the maximum amount of cheaters possible. 

Here's the problem in action:
https://old.reddit.com/r/linux_gaming/comments/18qk9m5/why_are_some_games_not_enabling_the_proton/kexagug/?context=10000

Given that my comment was under the highest voted comment on a popular post, it
seems likely that the people who saw it are a representative sample of
r/linux_gaming members. 

Me among others got consistently downvoted, and multiple different
non-AI accounts who engaged in "the behavior" in the replies consistently had a
positive upvote ratio. 

The consequences of this are harm all around. The community's credibility is
damaged, any request or claim from it will be met with skepticism. 
