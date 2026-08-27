---
layout: post
title: "Static Websites Are Great"
date: 2026-08-27 18:30:00
tags: 
    - tech
---

I recently rebuilt this site. I think it looks much better. I’ve had this website a long time: it started as a music blog, became a playpen for online projects, and now serves as my digital profile.

Once upon a time it ran on Wordpress. I dislike Wordpress: it’s [violently insecure](https://www.techradar.com/pro/security/experts-warn-2-000-hacked-wordpress-sites-were-secretly-running-a-global-crime-ring), horrendously bloated, and often costs money to host. It’s crazy that displaying text should require a database. Most of its features — comments, analytics — are YAGNI, and better handled elsewhere. It’s also hard to track, migrate, or access your own content.

Static site generators like Hugo or Jekyll solve every one of those problems, one for one. A static site is exactly that: nothing dynamic, so there’s no database to secure and no plugins to patch — simplicity is what makes it secure. Hugo builds this site for free, GitHub Pages hosts it for free, and CloudFlare throws in a free CDN — no hosting bill. And because every post is a plain markdown file tracked in git, I have a full history of every change, and the content is trivially portable to anywhere else — no migration required.

I’ve always been a fan of [Motherfucking Website](https://motherfuckingwebsite.com/) — crude title aside, most people just want to display text on a website, and simplicity gets you there fastest. Deploying works like any other software project: I can point Claude Code at any part of the site because it’s just text files in a repository, and the design is simple SASS and HTML, giving me full freedom over how it looks. Best of all: none of it depends on anyone else. All of it belongs to me.

This is probably the privileged take of someone who develops software for a living — I get it. If you don’t want to think about git and markdown, Wordpress or Medium will get you further, faster. But if you already think like a developer, there’s no reason to keep your content locked in someone else’s database. Build your website like the software project it actually is.


