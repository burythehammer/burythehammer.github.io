---
layout: post
title: "How do I do cross browser testing?"
date: 2017-03-16 10:53:00
tags:
  - testing
  - coding
---

I worked on a project where we had to do this. I'd say that the problem is closely related to cross browser testing, as you care about mobile / tablet browsers.

Doing this manually is not an option I would ever choose. Automation is going to really pay off, as these tests are very similar to one another but with a few tweaks, and your manual testers are going to get very bored doing them.

First off, you can use tools like Browserstack or Sauce Labs to simulate mobile phone/tablet browsers. It'll be a lot cheaper using those than maintaining lots of different browsers yourself.

We defined our test cases into three different form factors - desktop, tablet, and phone. The responsive design changed at certain resolution boundaries. So we did functional tests at all three main resolutions. We changed the browser resolution, and ran our standard functional suite against them.

I'd use techniques like a browser matrix and identify your most important audiences that you want to target. If you currently have a live website, grab the details from Google Analytics (or similar) and work out what you care about. Perhaps few people visit your website on a tablet, so you care less about it...?

How often you want to do this is really up to you. I'd probably do a normal functional suite every deploy to QA, and then more irregularly (perhaps every release candidate) do a full cross browser & responsive test. As far as the testing pyramid is concerned, resolution & cross browser testing is higher up than the acceptance suite - it takes much longer and you're not going to discover as many critical bugs.