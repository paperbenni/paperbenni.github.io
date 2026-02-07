---
date: '2026-02-07T14:48:21+01:00'
draft: true
title: 'Openclaw'
showToc: true
---


# Wishlist

Let me see a list of skills from Telegram commands. `/skill` does autocomplte,
but only the command name, not the skill name . I would love a `/skill list` or
just `/skills` which lists the skills with their descriptions. `/model` also has
an amazing menu way of browsing models, browsing skills in this way would be
really nice. Maybe you could even access clawdhub or whatever it's called
nowadays from the Telegram interface. 







How do updates to the AGENT.md and so on work?


Ideally the agent should not rely on its own SOUL.md or AGENTS.md too much. 
It self-modifies and as such could degrade over time. I have yet to see a model
aware enough of its own faults and quirks so it can prompt itself in a way where
it doesn't eventually degrade if the same model fed with that prompt is then
again modifying its own prompt. 


I want the agent to become smarter because of upstream changes. I do not want my
OpenClaw instance to become essentially a fork, requiring me to manually keep up
with new discoveries in how to get models to be more effective assistants. 

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
apart once the conversation centers around other things


