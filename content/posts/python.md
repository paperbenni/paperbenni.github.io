---
date: '2025-08-24T22:56:09+02:00'
draft: true
title: 'Python'
showToc: true
---

Whenever I work with python, things quickly devolve into marveling at what the
libraries can do and then fighting with them over types until I just give up and
read the source code or copy examples until things somewhat work. 

Pydantic AI's type hints are flat out incorrect. 

Different tools deduce types differently. Pyrefly detect 5 errors which do not
show at runtime, and which are probably because it deduced a type wrong. Pyright
and pylance both detect 1 error, which is different from the ones detected by
Pyrefly. This error is also not real, the script works just fine. 

This also translates into the programs which are actually written in python. 

I love ansible, but god I hate that it is written in python. It is huuuge. It is
slow. Its linter is even slower. The lack of good terminal libraries for python
is showing in how ugly its output is. 


Ansible galaxy is behind the times of 10 years ago. 
Upgrading collections is not a thing. You need to reinstall all of them. 




Astral-sh tools prevented me from hating Python

Why is Pylance closed source? Why do both Pylance and Pyright exist?
And then there's basedpyright?




