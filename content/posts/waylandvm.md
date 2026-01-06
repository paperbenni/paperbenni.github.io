---
date: '2025-11-26T14:31:11+01:00'
draft: true
title: 'Wayland does not work on VMs'
showToc: true
---

# Yes you read that right


I do not know how nobody is talking about this. 
Wayland does not work on virtual machines. It is not just slow, it is incredibly
unstable. I tested this out on VirtualBox and VMWare Workstation, and on both of
them, sway runs absolutely awful. Maybe Gnome has a way to plaster over these
problems, maybe it does not, I did not test it. Sway and Hyprland do not
even start with virtualized GPUs. 

Wayland is a protocol, a standard. Implementing the standard should be enough
for your application to become at least somewhat usable in the usage scenarios
the standard is intended for. 



Wayland is not supported in virtual machines


