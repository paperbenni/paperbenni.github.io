---
date: '2026-02-04T14:03:51+01:00'
draft: true
title: 'Aiarena'
showToc: true
---


I like the concept of LM-Arena (now called AI Arena, I will use both terms
interchangeably in this article)

I think it could be much much better. It has incredible potential, which is not
getting reached because of a few problems. Furthermore, I think these problems
are solvable and have what I believe to be realistic and doable suggestions on
how to solve them. 

Providing only leftover, unreliable or slow compute to lmarena should be
punished. 

Just like style control, there should be a control for shit infrastructure,
inefficiency and plain slow TPS. 

AI Arena is your marketing budget. You are providing free inference to testers
so that you can boast about your position on the leaderboard. The leaderboard
should in turn try to reflect the quality of the models. If being on top there
doesn't mean anything, then the top spot inherently has less value. The fact
that models which are a technical clusterfuck capable of only sometimes
producing a good answer are allowed to reach high-ish positions is bad both for
LLM companies as well as AI Arena. 

The prompts on AI Arena are not insanely long. Your time to first token should
not be insane. 

If you are taking a long time to respond to queries and often times even fail,
but only after letting the user wait upwards of a minute, that's bad for more
reasons than you might think. 

The obvious reason is you are wasting the user's time. Your model becomes a slot
machine, I wait a minute only for the model to fail responding. This is the
single most reason why I do not use AI Arena more often. It is an interesting
curiosity, and guessing models based on their quirks is fun, but the fact that
sometimes it just doesn't work means it's not suited for real work, which in
turn also means that that's not getting tested. If my chat has a 20% change of
just dying on every message, and slows me down a ton, I am not putting in the
work to actually engineer meaningful context. I will fire off a one-shot
message, keep the tab in the background and then check in on it a couple of
minutes later. I would argue this is not the primary use case for LLMs and does
not test their capabilities well. This is exactly what happened with LLama 4, it
was good at answering a single question in a very polite and convincing way and
then getting dropped. The fact that it all falls apart really quickly should not
have gone unnoticed that long and I believe the way AI Arent encourages its own
usage is partially to blame (apart from Meta inventing a new kind of
benchmaxxing)

The second reason is that you are wasting other people's inference. I can only
cast a vote on which model is better once both have provided an answer. If one
model gives me an acceptable answer in a couple of seconds, and another one
takes minutes and sometimes fails, I will likely close the chat after having
received one answer and never cast my vote. This robs the model which actually
works of an upvote. Not only that, the user never gets to see which model
provided the answer. I will repeat this again: AI Arena is marketing for LLM
companies, they can show off how good their models are. If I never get to see
which model actually produced a good answer then the entire point of it is moot. 



- ban providers/models which do not respond
- have a speed leaderboard






I get the idea behind style control

I do recognize that LLMs should not be trained to produce things which look
correct if you don't know if they actually are. 

That said, the fact that I have two models answering the same question means
that unless both are making the same error, I recognize that something is wrong,
and the model which very confidently claims to know exactly what it is talking
about while I know that it likely isn't gets an instant thumbs down. 

There is value in providing information in a format which is pleasant to read. 
If the information is correct, but incomprehensible to me unless I spend a ton
of work then this is a fault with the model. Outputs like that lead to code
which nobody bothers to read because it 'sort of works' and incorrect
information being skimmed over. 

LLMs need human supervision, and discouraging that by making models unpleasant
is bad. 

