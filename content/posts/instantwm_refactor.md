---
date: '2025-12-17T23:15:29+01:00'
draft: true
title: 'Instantwm_refactor'
showToc: true
---

Suckless kind of sucks. I truly do not get a lot of the design decisions. 

I decided to refactor instantWM, and I do have to say that I never knew how much
I improved as a programmer until I looked at the code I wrote while still in
school, having learned C by mostly just reading suckless code and applying
patches. 

flatcase naming
abbreviations
huge ternary expressions
bad naming
huge functions

Even if the point is that you should keep the entire source code in your head
which makes it really fast to edit, it's a lot easier to get the code into your
head if not everything has bullshit names or fancy one-line expressions. 

instantwm.c was just short of 7000 lines before the refactor. 
I get that instantWM did a lot more changes than most dwm forks do, but with the
way the patching system works, this is a state dwm forks naturally gravitate to. 

Patches generally are small enough to not warrant putting their code in
different files, meaning that the existing few dwm files constantly grow, even
if the compound impact of patches grows them beyond any reasonable dimension. If
multiple patches apply to the same function, but add things in different places,
then that function might grow beyond what anyone would consider maintainable.
Patches rarely split up functions, and refactoring existing code in a patch
means your codebase is then incompatible with most other patches. 

Another issue is the amount of magic numbers going on. I do not know if this 


Several functions had over 100 lines. 

A few things 


