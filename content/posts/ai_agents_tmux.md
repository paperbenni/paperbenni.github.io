---
date: '2025-09-25T19:47:27+02:00'
draft: true
title: 'Ai agents should be using tmux'
showToc: true
---

AI agents should run their commands in a tmux session. Claude code and most
other agents are horrible at running commands. It will run something requiring
user input and then get stuck. It may open a Vim session, fzf, or a dialog, and it cannot deal with that. 

I get that the problem sounds hard to solve, the easy way to implement terminal
commands is to do the following:

1. Have the LLM generate a bash command
2. Run the bash command
3. Wait for the command to finish
4. Feed the LLM the output and exit code of the command

The important part is that the LLM is not running while the command is running.
If the command requires input to terminate, then there is nothing to provide that
input and the command never terminates. The LLM never wakes up again, and the
entire agent loop is stuck. 

Another key factor is that LLMs do not support streaming input. They take the
entire prompt, ingest it and then start generating output (which does support
streaming)


Instead of running commands in the background, it should run its stuff in a tmux session.





