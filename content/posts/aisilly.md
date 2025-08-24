---
date: '2025-08-18T11:27:39+02:00'
draft: true
title: 'Aisilly'
showToc: true
---

# AI agent make silly mistakes

AI Agents have huge issues which are easy to solve, but which somehow nobody
bothers to solve. 



# Search tool calls

## Problems

You know the context size of your LLM. You know the size of the tool output.
Before passing it to the LLM.

it. is. going. through. the. IDE. first. 

YOU KNOW IT IS NOT GOING TO FIT. Or, in some cases even worse, it does fit. It
fills 99% of the context. The LLM will output a dozen very expensive tokens,
which will most likely be garbage, because its context is filled with 80%
minified javascript and 10% useless information. 

A single google search being done like this can cost you a dollar. 

Even firecrawl which is supposed to be used for AI does this. When looking up
the docs for a rust crate, it somehow managed to ingest the entire commit
history into GPT5-mini. 

Opencode is especially bad with this. It happily runs google searches using
a simple http fetch tool. Yes, that means tons of HTML/JS in the context. It
likes to fill its context 95% before even touching a file, and then crap out
because of either context rot or because it manages to stumble across a website
megabytes in size. 

Zed also fetches entire HTML sites into context, but is not as aggressive with
using google searches. 

Roo code does have a fetch tool, but I have never seen it voluntarily access the
internet. That's also a way to avoid the problem I guess. I've also seen it
resort to curl with the bash tool.


Claude code does this even weirder. It just doesn't have a search or fetch tool at all,
instead it relies on the LLM api to already do searches on its own. If an
'ordinary' LLM without server side tool use gets plugged into it via Claude Code
router, it just doesn't do google searches. 



## Solutions


Catch long tool answers before passing them to the LLM. Communicate to the LLM
that the answer was too long. That's the easiest. 

Also: Use a second LLM to extract the important stuff from the tool if it
exceeds a certain length. Even if it fits, it likely isn't all important to the
LLM. Give the second LLM the content, what information from it is needed and let
it do its thing. Summarization is already a thing with agents. They do it
whenever their context gets too large. 

Lastly: Good old web scraping techniques. An LLM looking for information is not
going to need minified javascript. It is not going to need tracking URLs. It is
not going to need links to stylesheets. It is not going to need most CSS
classes. We've had better things than `curl | my_expensive_llm` for a while now.
In fact, these things are probably what is being used to create the data sets
being used to train LLMs. Why not use them to make the result of tool calls more
readable for LLMs as well?

Again, firecrawl seems to come reasonably close to this ideal. It converts pages
to markdown. It even offers an Agent to do more complicated searches. That agent
is currently not available in the firecrawl MCP as of now, and also seems
overkill for most searches. I do not need cross referencing of multiple sources,
I just need a page, converted to markdown, with the irrelevant parts removed. 
As of now, as far as I can tell, this is not present with most coding agents. 

# Language integration

## Problems

If your code base is large, you cannot put it all in the context. 
If your code base is not shit, you don't need all of it to understand just a
part of it. 
You should be very selective about which parts of the codebase you put into the
context. If what you ask of the LLM is not a complete refactor or rewrite, then
it will need very specific parts of it. It will most likely start with listing
the files in your project and opening the ones most likely to contain the code
which needs modification or which relates to the feature request




## Solutions

LSP



