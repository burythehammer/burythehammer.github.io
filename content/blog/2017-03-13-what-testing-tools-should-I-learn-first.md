---
layout: post
title: "What testing tools should I learn first?"
date: 2017-03-13 19:00:00
tags:
  - testing
  - coding
---

Selenium is pretty good, and regularly used. It's definitely the industry standard for web tests. Avoid older proprietary tools (QTP/QC/UFT/Loadrunner) like the plague.

Cucumber, if doing user facing tests, is probably the other tool you'll see a lot. It'll run your tests, great reporting, hooks into CI pretty nicely, and makes very readable tests. You can get it for C# (specflow), Ruby, Java, Go, and lots of other languages.

I'd say it's worth finding a nice assertions framework, too. I tend to code in Java, so I use AssertJ. For Ruby, there's the RSpec Expect syntax which is nice.

Actually, Rspec in general is great, it's readable unit testing for Ruby.

If you're doing ruby based Selenium, check out Capybara and Site Prism. They're Ruby based DSLs which will make your life a lot more pleasant. Site Prism is great for doing the page object pattern.

Some more advanced topics if you're interested:

For performance testing, JMeter is more common, but I much prefer Gatling. I'd rather write Scala than XML, but maybe that's just me...

A (relevant) plug for myself, I've been doing a lot of stuff about cloud infrastructure testing recently - here's a summary a colleague wrote up. ServerSpec is the most popular tool, but there's also Goss and AWS Spec.

There's also something pretty cool called property based testing. In this you state the outer bounds of your functions/APIs, and the framework fuzzes lots of random data at your function and tries to find breaking edge cases. For python you can use Hypothesis, and for Java, QuickTheories.

