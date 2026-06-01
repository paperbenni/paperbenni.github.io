---
date: '2026-03-04T18:33:16+01:00'
draft: true
title: 'Opencode'
showToc: true
---


Wishlist

edit queue after submitting
delete messages from queue

No permission management UI
- adding a permanent allow permission like "bash -c ." is very easy, but it is not apparent how it can be taken back again
- same with allowed directories, what if I allow my agent to access `/` by
mistake? That is very easy, the agent will just ask you that, but not that easy
to undo. 
  


disable/enable MCP servers in UI

Configure plugins in UI

OpenCode plugins have not been doing great in general, mostly being replaced by
skills or using the opencode sdk directly. 

Preview for file edits like amp and cline (VS Code) have

When an agent is writing a long file, all the UI shows is `preparing edit...`.
If the agent is writing a file several thousand lines long, it can be useful to
know what it is writing while it is doing the writing. I dont want to know my
agent has gone off the rails 2000 lines in. 



ACP
- non-tool-call Messages disappear when closing and reopening zed
- bash tool calls just show a summary, not the actual command

exiting plan mode

The plan mode is a bit underbaked. The agent frequently gets stuck in plan mode.
The usual flow is talking about something, refining an idea with a bit of
conversation, and when all questions are answered, the agent eventually asks if
it should implement the plan. The agent does this expecting to not be in plan
mode after that. If you say "Yes, do it", then the agent will try to edit a
couple of files, run into the prohibitions plan mode imposes, and then either
give up or use injection attack its own harness to edit files with cat and sed.
If the agent uses the built in question tool to ask if it should proceed, then
that means I cannot switch modes before answering the question, and by that time
the agent will already be running in the wrong mode. And I will have a turn of
bullshit in my context. 



