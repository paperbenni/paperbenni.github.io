---
date: '2026-02-04T14:03:51+01:00'
draft: false
title: 'Aiarena'
showToc: true
---

# Stop wasting other people's money on AI Arena

I like the concept of LM-Arena (now called AI Arena, I will use both terms
interchangeably in this article)

I think it could be much much better. It has incredible potential, which is not
reached because of a few problems. Furthermore, I think these problems are
solvable and have what I believe are realistic and doable suggestions on how
to solve them. 

Providing only leftover, unreliable or slow compute to lmarena should be
punished. 

Just like style control, there should be a control for shit infrastructure,
architecture, inefficiency and plain slow TPS. 

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
machine, I wait a minute only for the model to fail responding or be dumb. This
is the single most reason why I do not use AI Arena more often. It is an
interesting curiosity, and guessing models based on their quirks is fun, but the
fact that sometimes it just doesn't work means it's not suited for real work,
which in turn also means that that's not getting tested. If my chat has a 20%
chance of just dying on every message, and slows me down a ton, I am not putting
in the work to actually create meaningful context. I will fire off a one-shot
message, keep the tab in the background and then check in on it a couple of
minutes later. I would argue this is not the primary use case for LLMs and does
not test their capabilities well. You do this with agent loops, not simple
chats. This is exactly what happened with Llama 4, it was good at answering a
single question in a very polite and convincing way and then getting dropped.
The fact that it all falls apart really quickly should not have gone unnoticed
for as long as it did and I believe the way AI Arena encourages its own usage is
partially to blame (apart from Meta inventing a new kind of benchmaxxing)

The second reason is that you are wasting other people's inference. I can only
cast a vote on which model is better once both have provided an answer. If one
model gives me an acceptable answer in a couple of seconds, and another one
takes minutes and sometimes fails, I will likely close the chat after having
received one answer and never cast my vote. This robs the model which actually
works of an upvote. Not only that, the user never gets to see which model
provided the answer. I will repeat this again: AI Arena is marketing for LLM
companies, they can show off how good their models are. If I never get to see
which model actually produced a good answer then the entire point of it is moot. 

The solution to this is already partially implemented in the form of style
control. To combat models spewing out false information with high confidence and
sycophancy to bait users into getting them upvotes, AI Arena punishes models for
doing so by placing them lower on the leaderboard than their raw upvote elo
would suggest. In the same way, models with high failure rates, high latency and
slow speed should also be placed lower on the list. I would argue that this is
even easier to implement because the technical quality of a model is an objective
metric. Drawing the line for what is style over substance in LLM responses is a
lot harder than simply counting the failure rate. 

If Gemini is incapable of ending its responses, resulting in infinite insanity
loops, that's a flaw in the model and should be visible on the leaderboard. 

If my model requires a bunch of retries until it answers a prompt, that should
be tracked and punished. The same goes for all other ways in which a model can
be bad apart from judging its answers if it eventually gives one. 

Furthermore, if a model fails a number of retries in a chat, it should
automatically receive a downvote and be swapped for another random model. That
way, a user can be sure that their query will get answered eventually. The
uncertainty when using LM arena is a huge blow to its usability. If I can be
sure that my prompt is getting answered by a working model eventually, then I am
fine with waiting a bit. If I have to constantly babysit the tab because I might
have to manually click retry or pose the same question in a new chat again, then
I am much more likely to just use another chat application. 

Finally, I propose a minimum reliability threshold to be even included on the
leaderboard. If a model is under that threshold it should not be served to
users. It would be cool if AI Arena could run automated tests for model
reliability and then start serving the model to users again once it reaches
acceptable levels of reliability. 



## Maybe AI Arena should go easy on the vibe coding

Not all the quirks with AI Arena are caused by model providers with bad
incentives. Some of them seem to be bad code on their end. Sometimes chats hang
indefinitely until I refresh the page, which then suddenly pops up the entire
answer. This means that AI Arena did receive an answer from the model provider,
it just forgot to relay that answer to me. This should not happen. AI Arena has
more money than OpenWebUI and T3.chat combined. OpenCode can show me model
failures in real time and has binary exponential backoff; any application
dealing with very unreliable APIs should have some way of dealing with that in 
a way that isn't just giving up and not telling the user, or retrying without
telling the user until they refresh the page. 

Please fix. Even if all current employees of AI Arena are vibe coders, I know
you have the money to hire real developers to fix this. It's doable, there are
hundreds of Open Source projects doing this better. 


## A side note

I get the idea behind style control

I do recognize that LLMs should not be trained to produce things which look
correct only if you don't know if they actually are. 

That said, the fact that I have two models answering the same question means
that unless both are making the same error, I recognize that something is wrong. 
The model which very confidently claims to know exactly what it is talking
about while I know that it likely isn't gets it an instant downvote. 

There is value in providing information in a format which is pleasant to read.
If the information is correct, but incomprehensible to me unless I spend a ton
of work then this is a fault with the model. Outputs like that lead to code
which nobody bothers to read because it 'sort of works' and incorrect
information being skimmed over. 

LLMs need human supervision, and discouraging that by making models unpleasant
is bad. 

On every new release, people are lamenting how the creative writing capabilities
of models decline further and further, and we might have gone too far in the
other direction from Llama 4. 

Most models nowadays put out acceptable tool calls and very recognizable
non-sensical prose inbetween those. Maybe this is a good thing, I'd rather have
them do work than try to be my friend. I don't know why this section is here.
Just food for thought I guess. 
