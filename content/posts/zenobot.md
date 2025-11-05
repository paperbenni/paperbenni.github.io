---
date: '2025-08-24T01:22:51+02:00'
draft: true
title: 'Zenobot'
showToc: true
---


I just had an idea for an AI assistant and I don't know if anyone else already
had that. If this already exists, then please tell me about it, so I don't
reinvent the wheel. 

# Tech Stack

Pydantic AI for Agents
SQLModel for Database with memories
Telegram Bot for chat access
Maybe FastAPI for management web interface


I also need to figure out a good way to deploy this and run database migrations. 

# Architecture

The assistant is made of multiple agents. 
They're roughly divided into two parts

## User interfacing

These either react to user input by replying, or contact the user proactively

## Memory gardeners

These work in the background to give the user interfacing agents relevant
context, and enable them to act proactively. They build system prompts in the
background before the user agents are ever called. They might for instance
change the system prompt of the reminder agent to contain an appointment the
user has to get to. If they can also figure out the travel time to that place,
they also put that into the system prompt for the next run of the reminder
agent. The reminder agent gets fed the current time and the background
information the other agents collected and decides to send a text message with a
reminder at the appropriate time. 

These iteratively keep the growing amount of memories in order and make sure
that the user agents can act on their own to support the user. 

## Memories

Memories are small to mid sized snippets of text. 
They can be searched via text.
Background agents can define relationships
between them, building a knowledge graph. 

## Gardening workflow

The gardening workflow should be triggered once a day, preferably at midnight. 


# Schema

## Memory

- ID
- Date
- content

## MemoryRelation

- From ID
- To ID
- Name

Example

```
From: Tom (ID 1231)
To: Peter (ID 1232)
Name: is the brother of
```

## Tag

- Name
- ID

## TagRelation

- Memory ID
- Tag ID

# Tools

## Store memory

Store information about the user
Query
```
Memory Content
```

## Request context

User interfacing agents can ask the gardening agents for context. 
The gardening agents can do their thing and then answer this with either

"Place the relevant memories in relevant"
or
"No memories found which contain the needed information"

## Delete memory

Delete a memory by ID. 
Query

```
Delete
```

## Read memory

Read a memory by ID

## Update memory

Change the content of a memory by ID

## Get related memories

Get a list of related memories

Query: Id of memory about Tom

output
```
Is the brother of
ID: adsasdd

2025-08-24T01:22:51+02:00

Peter
Phone number 821812831
```

## Relate memories

Establish a relation between two memories

Query
```ID From, Relation, ID To```


## Search memory by content

Query
```keyword```

Answer

```
No memories found, maybe try a different keyword. There might not be any
memories about this. 
```


## Fuzzy Search

## DeleteTag

Delete a Tag by Name

## TagMemory

Tag a memory, tag name and ID

## UnTagMemory

Remove a tag from a memory

# System prompt builders

## Relevant memories

All relevant memories without ID
This is meant to be used for append only agents

## Memories for gardening

All relevant memories with ID
A random assortment of other memories

All these should be sorted by date, regardless of relevant or not. 
This way the agent can easily tell if memories supersede each other. For
example:

```
2020
My favorite color is blue

2022
My favorite color is red
```

The Agent can deduce that the user changed their preference even though there
are two conflicting memories, and can remove the older one. 


# User Agents

## Chat

### Context

Currently relevant memories
recent chat messages

### Tools

Store memories

### Task

Chat with user and record memories

## Reminder

Context

- Relevant Memories
- Recent messages

Tools

- Send Message
- Save Memory

## Followup

Find incomplete tasks or memories which make no sense or are of no use without
more information from the user. 

## Critic

Find tasks the user might be putting off, find uncomfortable truths which can be
deduced from the memories. Try to push the user to become a better person.

### Context

Random assortment of memories and their related memories

### Task

Look for memories which are unclear and need confirmation from the user
Send that question to the user. 
After that, resume giving control to the chat agent. The chat agent will record
the answer, and other agents will then combine the memories. 

# Gardening Agents

## Deduplicator

Context

- Relevant Memories
- Random assortment of other memories
SORT ALL OF THEM BY DATE

Tools
- Delete Memory

## Aggregator

- Relevant Memories
- Random assortment of other memories
SORT ALL OF THEM BY DATE

Tools
- Read Memory

## Splitter

## Garbage collector

## Tagger

Context
- List of Tags
- Random assortment of memories (sorted by date), with tags they have listed

Tools
- CreateTag
- TagMemory

## TagCleaner

Context
- List of Tags
- Random assortment of memories (sorted by date), with tags they have listed

Tools
- DeleteTag
- UnTagMemory

## Relater

## ContextBuilder

### Task

Maintain the list of currently relevant memories
These get fed as context to all user interfacing agents. 
Examples of what this agent does: 

### Context
- Recent Conversation Messages
- Currently relevant memories
- Random assortment of other memories

### Tools
- TagList
- TagSearch
- MemorySearch

## Archivist

This should only be activated when the currently relevant memories become too
many. Also make sure this gets activated as the last agent in a gardening
workflow. 

Continue archiving until the amount of relevant memories is below a certain
threshold. 

### Task

Go through all currently relevant memories and determine which ones should go in
the archive. Memories should only be archived if They are not currently
relevant, but might become relevant again in the future. Memories which should
be deleted should not be archived, another agent will do that. 

### Context
- Relevant memories with ID
- Recent chat history

### Tools

- Archive Memory
- Count relevant memories


## Researcher

Not sure if this one has any use yet

### Context
- Complex Query which might require cross referencing memories
- Random assortment of memories

### Tools
- List Tags
- Get Tag Memories
- Search Memories
- Get Memory
- Get Related Memories


