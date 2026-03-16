---
date: '2026-02-07T14:48:21+01:00'
draft: false
title: 'Openclaw'
showToc: true
---


# Wishlist


## A retry mechanism

I am really really surprised this is not present already. Claude Code has it,
OpenCode has it, but OpenClaw does not. LLM providers are unreliable, harnesses
need to find a way around that. As of now, all I am getting is `Provider
returned error ERROR`. This is potentially catastrophic. The entire point of
OpenClaw is that the agent is proactive. I am not necessarily present to prompt
it to retry. If this happens on a cronjob, as it occasionally does, then that
job just does not get done. Even worse, for cronjobs and subagents, the prompt
was written by the main agent. I do not know the prompt, so unless I want to go
digging around json files myself, there is no way to manually retry that even if
I would want to. 

What I want is the agent to retry a failed request, increase the wait times with
each failure and eventually give up. When it gives up, it should TELL ME WHAT
THE ERROR IS AND AFTER HOW MANY RETRIES IT GAVE UP. It could be that a model is
no longer available, or that my API key expired or that I have run out of
credits or whatever, I would like to know that!!

## Better command handling on Telegram

Let me see a list of skills from Telegram commands. `/skill` does autocomplte,
but only the command name, not the skill name . I would love a `/skill list` or
just `/skills` which lists the skills with their descriptions. `/model` also has
an amazing menu way of browsing models, browsing skills in this way would be
really nice. Maybe you could even access clawdhub or whatever it's called
nowadays from the Telegram interface. 

As of now, `/skill` autocompletes, but running it does nothing, at least as far
as I can see. What would be even worse is if it just sends `/skill` as a prompt
to the model, but does not tell me that. In any case, the current solution is
bad. 


## Move critical behaviors and prompts out of config files

Over time, OpenClaw gains new capabilities and features. With a changing harness
and different tools, the model needs to be prompted to behave differently. 
It should not be my responsiblity to keep prompts and tools in sync. 

Any behavior that depends on tools and OpenClaw implementation details which
change frequently should not go in files which do not automatically update. 

Detailled markdown files with behavioral instructions instead of concrete tasks
should be treated like code, not data. I know that language models do not make
that distinction, but humans do. If behavioral instructions are in the user
config which gets created once and then is my responsibility, I have essentially
forked that part of the project. 

If the tools change, the prompts should change as well, and it should not be my
responsibility do do that. Keeping up with new discoveries in how to get models
to be more effective assistants is the maintainer's job, not mine. And if I do
make discoveries, I would like to upstream those instead of having them rot in
my own config. 

Ideally the agent should not rely on its own SOUL.md or AGENTS.md too much. 
It self-modifies and as such degrades over time. I have yet to see a model
aware enough of its own faults and quirks so it can prompt itself in a way where
it doesn't eventually plumet in performance. 

As an example, when I first tried OpenClaw (it was still called ClawdBot at that
time), I needed to instruct it which folder to use for memories. It used the
wrong folder and also did not create any memories proactively. 

It also had problems with skills. Skills are long prompts in markdown files with
special frontmatter which gets picked up by the harness. Instead of permanently
injecting the long prompt into context, the frontmatter contains a short
description, and the model can decide based on that which ones to pull into
context. It's an effort to reduce context usage (and rot) while retaining the
ability to give long and precise instructions for specialized tasks the model
might not know about. Skills are newer than most models, and even then, models
don't seem to have received post-training to make use of them. They don't know
the standard, and for existing skills they don't need to as the harness just
gives them the descriptions and instructions on how to invoke a skill. When
creating them, the model is sort of clueless what to do though. Expecting
ClawdBot to account for that, I asked it to create a pomodoro skill. It then
hallucinated a long pomodoro prompt in a reasonable but non-compliant format
into its memory instead of the skills directory. It took me a while to realize
that this is completely incorrect, because the skill partially worked. It could
use the read-file tool to "invoke" it and because the conversation was around
the pomodoro skill, it knew roughly what it was. This of course completely falls
apart once the conversation centers around other things. 

The fix for me was to instruct teh model to read the skills specification before
creating a skill, and persisting those behavioral instructions in its memory. 

Nowadays, there is some prompt injected into context which contains more
concrete skill format instructions whenever the model creates a skill, and there
is a skill template which the model can gradually modify. This is a way better
approach than what I did before. I would like to see more of that, in fact,
there should not be a single tool or behavior in OpenClaw which requires the
user to write programming like prompts into TOOLS.md or SOULD.md or any other of
the user config files. My initial approach was wrong. Had I not noticed the new
upstream prompt injection, the model would have been stuck with two potentially
conflicting instructions when asked to deal with skills, which would waste tons
of reasoning tokens on second guessing and result in worse outcomes. 

The solution in my opinion is to keep only data-like or preference like
information in config files, and expand the capabilities of the harness instead. 

Do not introduce any features which confuse the agent if they are not used with
programming-like prompts. Programs can have bugs, and if I program in a
non-deterministic language on top of 400k lines of typescript slop, then I will
have even more bugs. 


