---
date: '2026-01-07T12:58:19+01:00'
draft: false
title: 'Kilo Code CLI'
showToc: true
---

# My experiences with Kilo Code CLI

TLDR; don't bother, this is unusable. 

Take the model switcher for instance. You might expect to type /model and then
be prompted with a list of models to choose from. You might use arrow or vim
keys to navigate the list, maybe even type to filter the list. 

Well fuck you, that's not happening. It brings up a help menu which claims you
need to use `/model select <modelname>` to select a model. You type that,
autocompleting the select command, expecting to get a model list to choose from
just like you got a subcommand list. No can do, delete what you typed, you need
to use the list command to actually get the model names. You then manually copy
the model name from that (If you're unlucky, you have to use the awful
pagination system, typing `/model list next` a few times. 


The input line is awful. The bare minimum I expect nowadays is readline or
something emulating it like Claude Code does. Or just give me the ability to
type the prompt in my own editor, again, like Opencode and CC do. 
(Well the only exception for some reason is Ctrl+U, which clears a line, but
pressing it again does not delete it)

Kilo Code CLI does neither. No ability to move around word-wise, no ability to
delete an entire word, or an entire line, no ability to jump to the beginning or
end of a line, pretty much everything nice about working in a terminal is gone. 


The layout is incredibly strange and wasteful. There are three bars at the
bottom, each of which take up three lines. Below them is a bunch of completely
empty lines. Effectively 40% of your screen is wasted space. The bottom bar
shows your status, the middle bar is the actual input line, and the top bar is
some nano style hints. The bottom bar has no reason to have padding and an
outline, as its content is very predictable and it is separated from model
outputs by the input bar anyways. The top bar is completely redundant. It shows
the help, mode and shell commands. I do not know why they didn't add more, as
the bar is mostly empty space. Besides, the input bar already shows how to use
commands when empty, and the first thing which appears when you type a slash is
a completion popup showing the same commands, with the help command at the top. 
Why do I need the top bar if the input bar tells me the exact same information
in a nicer way?

The entire thing feels like designed by a non-vision-LLM. 
Kilo Code is a nice free MiniMax token dispenser, but the actual harness is bad. 
I would love to use the Kilo Code gateway with Opencode instead, but that kind
of defeats the purpose of the free trial, so I guess that is unlikely to happen.



