---
date: '2026-03-21T11:15:44+01:00'
draft: false
title: 'The biggest DLSS 5 problem nobody is talking about'
showToc: true
---

DLSS 5 has proven quite controversial for how it looks and how it changes the
way things look from what the original artists intended them to look like. 

I think that DLSS 5 has a much much bigger problem that Nvidia has not even
begun or attempted to address. A big problem for AI video generators has always
been temporal stability, and Nvidia is very proud of their achievements in this
field. The traditional problem is the following: If the AI recognizes a patch of
grass and puts grass blades there, and then does the same for the next frame,
the blades will likely be in a different arrangement. Nvidia aims to solve this
by giving the AI access to motion vectors as well as a few of the past frames. 
That reduces flicker when looking at a still scene, or when moving around. 
Here's the thing though: Games are longer than a few frames, and often give the
player the ability to view things from different angles, leave an area and then
come back much later and a lot more. 

DLSS 5 can change facial features, textures, lighting, colors, and regardless of
wether or not you think that looks good (I mostly do not think it does yet, but
it has the potential to), it doesn't matter if it does or ever will. It looks
meaningfully different from the original. What happens if a character walks off
screen and then comes back? DLSS 5 only has access to the a few frames and
motion vectors, it has no memory of the character once they have been off-screen
for a few seconds. Even if it did, how about a character which has been
off-screen for minutes or hours? Every time that happens, DLSS 5 will take a
brand new guess at how that character is supposed to look like. DLSS 5 would
need to keep a permanent memory of all characters in a Game. When playing with
DLSS 5, will I ever recognize side characters which only appear every so often?
If they repeatedly age forwards and backwards by decades, change their hair
color and facial features all the time, is how they look even important then?
Even if you did introduce a feature which allows DLSS 5 to permanently memorize
characters, what happens if a character actually does age or change in some way
in the game? DLSS 5 will have to have an understanding of the entire plot to not
mess that up. 


Let's go back a few years and look at screen space reflections. These work by
mirroring an existing image to simulate reflections instead of rendering a
second image from the perspective of the reflective surface. if I look down at a
puddle of water, reflections of things not visible through other means
disappear. Often, this is masked by the reflections being blurred or distorted,
or by fading them out as the viewing angle approaches 90 degrees. This exact
kind of artifacting has been a problem in forever, and is one of the reasons why
we have raytracing in the first place. 
You had to be careful how and when to use screen-space reflections in order for
the artifacting to not be too visible, and with ray-tracing the artifacting
doesn't really exist, apart from a bit of noise. 

DLSS 5 is a screenspace effect for literally everything, it has no spacial
awareness. What happens if I look at something which is clearly a colored light
source, and then gradually look away from it? My guess it DLSS 5 will put
colored lighting on things, and even if the light source goes off screen, the
colored lighting being in the last few frames will mean that it will deduce that the
next picture will also have the colored lighting. What if I entirely turn away
from it and then turn back to the area which was previously colored by the light
without revealing the light source itself? The model has no idea there is a
colored light source just outside the field of view, so the area will have
returned to its normal color. What happens if I then pan further to reveal the
light source? Will the entire picture then snap back to being colored again?
Or what happens if a light source gets destroyed off-screen? There is no way for
DLSS 5 to know that, it would have to have access to engine specific metadata. 
Will it try to find a middle ground and just fade out any light source no longer
on screen? What happens when it completely guesses where light should come from
because no light source is on screen, only for the sun to become visible and
reveal it was completely wrong. Will it then fade towards a more appropiate
light setup or will it snap to something more appropriate, leaving us with a
jarring transition? Both approaches can go horribly wrong. Any fading will mean
ghosting. What happens if a light source gets occluded, what happens when I
close a door to a room without lights? I will always have lingering light, and
what the model imagines that light would make visible. If there is a harsh
transition, then any time a light source simply goes off-screen, things will
look horrible. 

Yes, developers will be able to exclude parts of the image from being processed,
but screen-space effect artifacts being able to popup ANYWHERE and EVERYWHERE as
opposed to rivers, mirrors and puddles only will require a shit ton of masking
just about everything. 

I sincerely hope Nvidia changes their approach. I could see this kind of
technology working somewhat if developers could fine tune the model on
individual characters and environments and assets, and the amount of shit it
pulls out of thin air gets lessened. Imagine, you could fine tune the model
based on a bunch of images of a high quality model or actor, and then
drastically reduce the poly-count of the actual in-game 3D-model to only give
the AI enough information to guess which character or asset is supposed to be
where. Maybe also produce a bunch of images of the characters and assets being
in the actual environments and lighting conditions that are supposed to be in
the game, with ray-tracing, path tracing and all sorts of effects that would be
impossible to achieve in real time, and also fine tune the DLSS AI on those. 
That would enable preserving the intended look of the game, while enabling the
use of effects previously only possible in pre-rendered movies, like a new form
of baking, but not just for static lighting. 

That would take actual artistry and skill though, so I'm guessing Nvidia doesn't
like it. Please prove me wrong though. Please. 



