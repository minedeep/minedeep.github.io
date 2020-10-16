---
layout: post
type: post
title: "Working with SSH"
date: 2020-10-15
categories: technotes
comments: true
author: "Hailey Do"
tags: [machine learning, deep learning, python, ai, ssh]
header-img: /assets/png/how-to-debug/Blog-TitleCard.png
description: |
    Working remotely over SSH is . In this blog, I share my own debugging "mental framework" through
    some pixel art!
excerpt: |
    It seems that any software engineer is expected to know how to debug.
    However, there's not much material or structured framework on how to
    do it. In this blog, I share my own debugging "mental framework" through
    some pixel art!
---


## Introduction



**Debugging seems to be a skill expected from anyone entering into tech, but
the knowledge on how to effectively do so is siloed-out.** It makes sense
because as you learn how to code, you've certainly hit errors and 
debugged your way out of it. Then, as we went through our own tech journeys, we
developed a tacit knowledge[^1] on how to debug.

> I realized that I don't have a "mental framework" on how to debug
> effectively. Usually, I just rely on my tacit knowledge and
> practical experience.

I realized that I don't have a "mental framework" on how to debug effectively.
Usually, I just rely on my tacit knowledge and practical
experience. Hence, I devised a short three-part framework for myself, and I'm sharing
it to you through Pixel Art[^2]!

## Code R.E.D.: my mental framework for debugging

![](/assets/png/how-to-debug/Blog-TitleCard.png)


The color red hints at urgency, just like those movie scenes where enemy aliens
attack and emergency alarms are set off&mdash;that's how I see the process of
debugging. 

R.E.D. is also an acronym for the mental framework that I'm trying
to practice: it sounds nice, and on theme with my Space Force pixel art!


### R is for Reproduce

![](/assets/png/how-to-debug/Blog-CodeRED-Reproduce.gif)

One of my first steps in debugging is to reproduce the bug in a controlled
environment. I do this in order to confirm that the bug exists, and to isolate
it given a minimum set of variables. 

I reproduce bugs by ensuring that I accomplish the following in my project:

- **Create a minimum working environment**: this may include the version where
    the bug was discovered, dependencies, error/stack-trace, and a ["minimal, complete verifiable
    example"](https://stackoverflow.com/help/minimal-reproducible-example). For
    my open-source work, I automate this using [Github's Issue templates](https://help.github.com/en/github/building-a-strong-community/configuring-issue-templates-for-your-repository).
- **Setup my project so that it's easier to reproduce parts of the code**: I do
    this by pinning dependency versions, writing readable logs and error
    messages, and keeping an updated local dev setup instructions.



## Conclusion

In this blog post, I talked about my Code R.E.D. framework on debugging. It's
an acronym for a three-step process that I follow whenever I want to squash
some bugs: *R* for **Reproduce**, *E* for **Execute**, and *D* for
**Document**. I also explained some practices that I follow as I go through
each step. You might notice that these guidelines are still rough, but I think
that having a simple methodology on how to approach debugging is helpful. 

Lastly, I hope that you enjoyed the Pixel art, and adopt the Code R.E.D.
framework into your own workflows! If you wish to see more of my fledgling
attempts in pixel art, follow me on my Twitter art account,
[@pixineries](https://twitter.com/pixineries)!

P.S. Here's the full Pixel Art GIF!

![](/assets/png/how-to-debug/Masterfile.gif)


### Footnotes

[^1]: I think of tacit knowledge as know-how that is not explicitly defined&mdash; like riding a bike.
[^2]: Yes, I've been learning pixel art for the past month!
