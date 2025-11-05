---
date: '2025-10-03T12:00:52+02:00'
draft: true
title: 'Ai pricing looks illegal'
showToc: true
---

# High prices are not the biggest problem

What you get charged for cloud services depends on how much stuff you use and
for how long. Measuring that amount is up to the cloud provider. The cloud
provider gets more money the higher the usage measurement, and is also in charge
of taking the measurements. That is technically a conflict of interest. I cannot
verify when Google tells me that my site received a lot of traffic, so in
effect, Google can tell me what the price for their services is after I
obligated myself to purchase them. Until now, the "trust me bro" has worked
remarkably well. We can check if the measurements are somewhat plausible, and if
you are a CRUD company, cloud charges are peanuts anyway. The assumption always
was that if a cloud provider was caught lying about resource utilization their
reputation would be ruined, so there's a strong incentive to be honest.
Or so we thought I guess. 

I do not comprehend how what most AI companies do is even legal. 
Shouldn't a purchase come with contractual obligations for the party I purchase
something from? Isn't that the entire basis of the service industry?
The way it is right now is "you can give me money to purchase a nebulous
*something*, I will maybe tell you after the fact what it is, or I will not and
you can guess, and even if you guess correctly once, I might halve my services
at some point without telling you." 

If we set a precedent that a big company can get away with slashing their
services by 50% without telling anyone, then that will have bad consequences for
the entire industry.

AI subscriptions are the biggest culprit here. GitHub copilot used to be
"unlimited", and as with anything unlimited there are of course limits, but
unless you are doing something crazy, the expectation was that you would never
reach them. Anything with limits which you could realistically reach with a
normal amount of usage has them displayed clearly. Internet via 4G is limited,
and I have a meter for that. Cloud storage has limits, and I have a meter for
that as well. My home internet is unlimited because I am not capable of
realistically reaching its actual limits.

And look where we are now. GitHub Copilot started introducing limits at an
unknown point in time, people just started seeing error messages when using it.
At first those were hourly limits, although we can just guess. After getting a
few rate limit messages, after a few hours, Copilot started working again.





# NOT EVEN TOKEN BASED PRICING IS SAFE

I noticed the following message on the Factory.AI dashboard

> Standard tokens now apply to any models. However, premium models use 7x the
> standard token count.

At first glance, it seems reasonable to charge more for a premium model. IF ONLY
I KNEW WHAT A PREMIUM MODEL IS. This is documented nowhere. Is it anything
except the mini models? Is it Claude Opus or Grok 4? Is it GPT-5 High or even
regular GPT-5? Who the fuck knows, certainly not the documentation, pricing page
or AI assistant of that company. Also a 7x price increase is insane.
Disregarding the fact that we do not have a baseline of what a 1x model is, if
we assume it's something like GPT 4.1 (which Copilot does), then there are no
models on the market which are 7x more expensive. Sonnet is about 2x more
expensive, Opus is about 9x more expensive. Does that mean Sonnet is a premium
model? If I am already getting charged 7x, can I just use Opus instead of
Sonnet?

Also, Factory.AI supposedly does token based pricing. There's a token meter on
the dashboard, and you can buy tokens. But what the hell is a token in their
mind? If a model can "use 7x tokens" does that mean a single token from those
models gets counted as if you used 7 tokens? Is that referring to output or
input tokens (which are way cheaper to compute)? What about reasoning tokens?
Does a single input token get counted as 0.2 tokens, and with the premium models
as 1.4 tokens? Then at that point, why do you call the unit "token"? It's
clearly something different. 

Grok and Gemini also aren't transparent about their pricing even with the token
based APIs. Their models are reasoning models, but they both do not give the
customer access to the reasoning tokens. They just tell you how many reasoning
tokens you supposedly generated and then charge you for that.



