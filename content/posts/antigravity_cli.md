---
date: '2026-05-20T15:30:06+02:00'
draft: false
title: 'The Antigravity CLI is a disaster'
showToc: true
---

# The Antigravity CLI is a disaster

## Awful permission management

The CLI requires you to constantly babysit it, because it concludes that running
typechecks is dangerous 10 times in a row. 

My guess is that the model is aware that compiling Rust can execute arbitrary
code, meaning that cargo check is technically never safe. It does however
happily add permanent permissions to the CLI for executing shell scripts it has
the ability to edit without my approval (yes, file editing permissions are
missing from the CLI, I cannot prevent it from editing files). 

## Awful edit displays

The TUI is entirely broken.

The input bar shifts up and down at random. The artifacts feature contains hyperlinks
which do not do anything when clicked. 

It always displays paths as absolute paths. This means that I get to see my home
directory, as well as the end of the path, but not where the file is actually
located. 
Example

```
/home/benjamin/workspace/...r/mod.rs
```


What the hell am I supposed to do with that? Also, my terminal is hundreds of
characters wide, something the rest of the CLI has absolutely no problem abusing
the hell out of with the model happily producing very long lines which get
displayed without any line breaks in them. The full file paths would fit. Or
even better, display what project I have open somewhere in the UI and display
paths as relative to the project root.


## No subagents

I will die on this hill, subagents are a non-negotiable feature for any LLM harness. 
When exploring a codebase, agents grep and read lots of files, only a subset of
which will be relevant to the task at hand. 

Even if you do not consider subagents to be as important as I do, the Gemini CLI
had them, and the new CLI does not. Neither have I ever seen the Antigravity GUI
use a subagent. 

I don't believe that Google as a whole disagrees with me about the importance of
subagents, I just think the people making decisions about the CLI are too
incompetent or starved for time and resources to implement them. 


## Closed source

The Gemini CLI was open source, the Antigravity CLI is closed source. 

I have no idea why they did that. Did they see the Qwen CLI and ob1 and feel
threatened? Do they think the Antigravity harness is their "secret sauce"?
Is Gemini regularly pushing .env files?



## No ACP support

Gemini CLI was the first LLM CLI to support ACP, even partnering with Zed
directly to make it good. The new leadership seems to be arrogant enough to take
a more hostile stance towards the outside world, even though they have nowhere
near the performance lead or even any quality to justify that level of snark. 

People mostly put up with Claude Code because it offers cheap Opus inference.
Anthropic acts openly hostile towards its customers and the Open Source
ecosystem, but because their models are good, they still don't lose an insane
amount of customers. If Anthropic is a charming and wealthy but abusive partner
you keep coming back to, then Google is one which is just abusive and really weird. 

Add to that the fact that even though Claude Code might be a vibe coded
overengineered monstrosity, even though it probably costs orders of magnitude
more to develop (including buying bun outright) than something like OpenCode or
Zed or the Copilot CLI (yes, that is actually usable these days, even though the
rate limits are not), it does somewhat approach their quality simply by virtue
of the amount of money being thrown at every problem it has. 

It looks like Google cannot even be bothered to do that. 

Google is behind when it comes to raw model performance, and even when it comes
to price to performance. Other providers have been able to balance out their
lack of intelligent models with other factors. If I am not the smartest person
in the room, people might still want to work with me over that person if I am
simply nice and the smartest person is an asshole. ACP is part of being nice. 


## Go

This is the one upside of the new CLI. It is written in Go as opposed to
TypeScript. The old CLI had hiccups and freezes and very high resource usage,
the new one does not. It is a bit disappointing they did not move to fullscreen
rendering or offer the option to choose between the hybrid TUI and a full TUI.
This means I cannot select text without also copying the decorative unicode
elements, as the CLI has to rely on the terminal emulator to do selection. It
also means that I am limited to the truncation limits of whatever terminal
emulator I am in, and in the case of a tty I have to go without scrollback
entirely. 



## Gemini 3.5 flash

This probably warrants an entire post on its own, but the marketing is very
misleading. The most important metrics for LLMs are quality, cost and speed,
probably in that order. 

Speed is easily the least important of the three. I am waiting a
non-deterministic amount of time when giving tasks to an LLM, any workflow using
them should be asynchronous enough for sub-order of magnitude response time to
not be of serious concern. If the output is of low quality and very expensive,
it doesn't matter that I do not have to wait long.


