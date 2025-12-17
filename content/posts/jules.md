---
date: '2025-12-17T20:16:07+01:00'
draft: true
title: 'Jules'
showToc: true
---

My thoughts on Google Jules

I am not paying for the product, I get the pro version for free, yet I am still
upset wit you. 


Here's a list of frontend bugs:

There's no paging or chunking in the conversation. If Gemini - as it likes to
strangely do - (yes that is an em dash, I am not an LLM) decides to dump its
thinking traces in the chat or the code again, the chat baloons to an insane
size. The way the frontend works, a conversation is either present or it is not.
Every single message needs a DOM Element and all of these rerender far too
often, leading to my browser crashing or being unresponsive for tens of seconds
when switching chats. 

The line wrapping does not work. 
Messages seeminly at random are really wide and partially cut off. 

The diffing does not work. The displayed numbers are sometimes correct,
sometimes they are the number of changed hunks (???), at least that is what it
looks like. 

## The agent is bad

The edit tools sometimes do not work. This means they sometimes report a
successful edit even though they discarded the edit. 
Either that or the system prompt is exceptionally garbage. I have never seen
Gemini 3 fail 20 tool calls in a row in multiple conversations with mostly
distinct context. 
This means either the tools are unreliable, leading to the frequent message
"maybe I am insane" from the models, as it has no idea what the state of the
codebase is like, or they managed to make Gemini 3 even more quirky than it
already is. 

There are other issues with the agent. 

As far as I can tell it does not read documentation or do any other research
while coding. Only during planning does the UI show that the model actually did
some Google searches. The point of Gemini is that it should pretty much always
be able to do Searches, looking at the company who owns it and its primary
purpose. But I honestly do not think that the model has access to search tools
outside of the planning phase, which means that if it hits an unknown library method
which it did not research beforehand, it guesses a bunch of names and parameters
and continually compiles until one works. With that trial-and-error loop in its
context (which does not seem to get cleared out or compressed, just truncated)
it only needs one more failure to go completely insane. It forgets how to use
tools, starts editing code exclusively with sed and cat, and writes dump grep
queries which each output half the codebase. 

The agent cannot use interactive tools. For other agents this is not as much of
a big deal because the user can always interrupt the agent, tell it not to use
that tool and then do whatever interactive process the agent triggered
themselves. With Jules this does not work, because the user does not even get to
see what tools and CLIs the agent tries to use until after the fact when it
sleeps around whenever it encounters an npm or fzf prompt, and then wakes up
once the command times out. 

I have no way to configure or access the environment it is running on. The
environment seems to be a standard debian/ubuntu VM, which the model has root
access to. This means the model can fundamentally break things. If the agent
manages to break something fundamental, all the code and context is gone, I
cannot just reset the env or undo whatever it broke. 

There is no task list like in Claude Code, at least none the user can see. The
model creates a multi step plan, but at no point is it obvious when a step from
that list has been completed, and the harness does not seem to remind the model
of any tasks from that initial list which are unfinished at the end. 

The adverserial code reviewer agent would be a nice idea, if it actually got
activated, because often times it just doesn't. I do not get how this gets
determined, but in case the model itself gets to decide if it wants its code
reviewed then that defeats the purpose of the review. 



