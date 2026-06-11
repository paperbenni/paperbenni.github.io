---
date: '2026-03-16T18:28:34+01:00'
draft: false
title: 'Openclaw_containers'
showToc: true
---

OpenClaw cannot be containerized. I'm calling it. "I ship code I never read" is
bullshit. DevOps is safe from being replaced by Codex for now, holy crap is it
incompetent in this area. The deployment process of OpenClaw is a nightmare. I
don't mean this as in "I want it on the App Store, where is the exe smelly
nerds" kind of way, I mean that even as someone who has worked in DevOps and who
has developed an Arch Linux installer, the experience and outcome is bad. 

The docker-compose file contains a bunch of environment variables. The file
itself is not meant to be used as-is, if you do that you will end up with a
non-functional installation, as the gateway (which is for some reason what they
call the primary server) enters a crash loop when its json config files are not
set up before it even starts. Shelling into the container also does not work
because of the crash loop. Instead, you are meant to use the docker-setup.sh
script (aptly using a different naming convention than the setup-podman script). 
If you are under the assumption that this script will set up the missing
environment variables or ask you for any information to create them, then you
are incorrectly assuming Peter has ever looked at or even executed that script. 
It just proceeds to build the entire docker image locally, so you get to watch
it eat tens of gigabytes of disk space, which means your cheap VPS is probably
not going to be able to handle it and you are ending up with an empty gateway token
(which is what they call their API keys). Even better, the produced json config
is still invalid, and you end up with a dead container, which is derived from
the same image as the gateway, which doesn't seem to do anything really. Because
the produced config is still invalid (the onboarding process is only meant to
produce valid config for bare-metal non-sandboxed installations), you still end
up with a crashloop, which means you cannot even edit the config. By default,
named volumes are used, so you cannot easily edit the config while container is
not running. The solution is to make the startup command a really long sleep, so
you have enough time to shell into the container and edit the config there.
However, the error message which caused the crashloop references a config value
which is nowhere to be found in the official documentation, so I am expected to
throw codex at the codebase and spend a few dollars just to potentially maybe
find out what is going wrong. 

I am at this point convinced that the crowd hyping OpenClaw has never heard of
docker-compose or Ansible, nor read any of the `curl evilshit.sh | bash` scripts
they run. How the hell are all the OpenClaw forks advertising how lightweight
they are? OpenClaw itself takes less resources than a browser, in theory it runs
on a 1GB Oracle VPS. In practice, deploying it takes infinitely more resources
than to run it. 


