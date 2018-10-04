---
layout: post
title: "Shadow Functionality"
date: 2018-10-04 12:30:00
tags: 
    - testing
---

When making software, the process for making features is theoretically straightforward. You design the feature, it gets groomed, chopped up into tasks, and these tasks are implemented one at a time. The feature is then delivered. This process implies that all functionality of a system is deliberately designed. 

However, this is not always the case. 

Some colleagues at a previous job were working on a shopfront for their clients. They discovered that there was a security vulnerability - raw javascript was allowed in some of the text boxes. This could be abused in all manner of ways, and was definitely not intended by the development team. However, when the devs proposed that this flaw be patched out, they received pushback from their users. The users actually used this flaw in the system to add extra functionality to their shopfronts. In fact, many shopfronts _relied_ on this customisation, despite it being unintended. So the devs were stuck between removing a security risk and maintaining current functionality in their system.

You may be familiar with a term called [Shadow IT](https://en.wikipedia.org/wiki/Shadow_IT). Shadow IT is when parts of an organisation adopt IT processes and tools that are not explicitly approved by the wider organisation. It can often because the tools and processes that they _should_ be using are inadequate, or are not perceived to be.

In a nod to shadow IT, I've started calling unintended, yet useful features of your system "Shadow functionality". If your users are using your system in ways you didn't intend, you may want to think about whether the official, intended ways of doing things are the best - and how your userbase may react if you clamp down on unofficial usage. You may also want to be far more careful about testing your features before they are released!

Experienced testers, I expect, will be familiar with this. I'm a videogames fan, and I see this happen a lot. Players often cheat in games, or exploit the software, to get ahead. But cheating and exploiting aren't necessarily the most fun ways to play a game. Or maybe players aren't playing the bits of the games you intended to, because other parts were more fun!

This idea is closely linked to the idea of software [desire lines](https://en.wikipedia.org/wiki/Desire_path). However, I feel there is a subtle difference. Desire lines are more benevolent - a workaround whilst trying to use the software, which points to issues with usability. Shadow functionality is more along the lines of a widely used exploit. There is perhaps some sort of conflict with security or performance, and it has a manevolent or more murky connotation. 

This said, there is a common ground here: users don't always use your applications in the intended way. It's so important that we are in touch with what our users want, and how our system is being used. This means monitoring production, user feedback, exploratory testing sessions, usability testing. Don't be in the dark!