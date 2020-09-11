+++
title="The Alfred Emoji Pack (with skin-tone modifiers)"
date=2020-05-03
description="If you're an Alfred user, you can use this pack to expand snippets for emoji shortcodes. 💪🏻"
+++

👋🏿👋🏾👋🏽👋🏼👋🏻

To install, just follow the appropriate link:

* 🙋🏿 [Emoji Pack (Dark Skin Tone)](https://github.com/tjwds/alfred-emoji-fitzpatrick/raw/main/dist/Emoji%20Pack%20(Dark%20Skin%20Tone).alfredsnippets)
* 🙋🏾 [Emoji Pack (Medium-Dark Skin Tone)](https://github.com/tjwds/alfred-emoji-fitzpatrick/raw/main/dist/Emoji%20Pack%20(Medium-Dark%20Skin%20Tone).alfredsnippets)
* 🙋🏽 [Emoji Pack (Medium Skin Tone)](https://github.com/tjwds/alfred-emoji-fitzpatrick/raw/main/dist/Emoji%20Pack%20(Medium%20Skin%20Tone).alfredsnippets)
* 🙋🏼 [Emoji Pack (Medium-Light Skin Tone)](https://github.com/tjwds/alfred-emoji-fitzpatrick/raw/main/dist/Emoji%20Pack%20(Medium-Light%20Skin%20Tone).alfredsnippets)
* 🙋🏻 [Emoji Pack (Light Skin Tone)](https://github.com/tjwds/alfred-emoji-fitzpatrick/raw/main/dist/Emoji%20Pack%20(Light%20Skin%20Tone).alfredsnippets)
* 🙋 [The Original Emoji Pack](http://joelcalifa.com/blog/alfred-emoji-snippet-pack/Emoji%20Pack.alfredsnippets)

**Then be sure to uncheck "Strip snippets of 'auto expand' flag!"**

👍🏿👍🏾👍🏽👍🏼👍🏻

## The why

I've been a regular macOS user for over a decade now, and I love the Spotlight model of launching applications.  It's basically baked into my brain that every app I open will be launched by typing its name, no matter the context.

Since I've already built up this muscle memory, I'm really enjoying my recent exploration of Alfred.  Though it's taken some time to retrain some habits to redirect them to that Alfred motif, it's so great to be able to interact with even more parts of the tools that I use with this same process.

Alfred doesn't just provide a Spotlight replacement; it also provides other productivity tools, like text replacement when you type certain keys.  For example, here's a UUID I created by typing `:uuid:`:

> BEFE04B5-2B41-4FF3-BAF2-54632CBFF8AF

I also use emoji a lot when I communicate.  Especially recently, with most of my communication with coworkers happening over Slack, it's important to be able to convey my personality and come across as having a positive demeanor.  I've optimized my use of emoji so that I just automatically type the universally-accepted shortcode for each emoji, like :+1: for 👍🏻.

[Joel Califa created a pack of snippets](http://joelcalifa.com/blog/alfred-emoji-snippet-pack/) to automatically replace those shortcodes in all contexts, so that right now, in my text editor, I could just type :bee: and get the 🐝 emoji.  However, these use the unmodified human emoji, which I don't use — as you'll see above, I've decided to use emoji with the Fitzpatrick modifier the represents me.

Instead of attempting to describe why this snippet pack is so cool, I'm just going to point at Joel's blog post above — it does a much better job of describing all the use you can get out of it and the problems it solves than I ever could!

## The how

So:  how does this work?

Big thanks to Joel, who responded for my request to make derivative work from his original emoji pack within 10 minutes of my sending the message to him!  I'm really appreciative the he both extended this permission but was also excited about the project.

You can find the code that generates these emoji packs in this Github repository: [https://github.com/tjwds/alfred-emoji-fitzpatrick](https://github.com/tjwds/alfred-emoji-fitzpatrick)

As for the implementation, it's fairly straight-forward:  we iterate over the list of shortcodes provided by Joel, replacing any appropriate emoji, and and assigning new GUIDs.  This creates five directories, which I can then import into Alfred to create an exportable snippet pack.

## The future

I think there are a few more things that I could do to improve these packs:

First of all, the process for distributing these files is a little onerous.  The snippet packs are just zipped directories filled with json files with a manifest; theoretically, this should be something that I can automate.  So, next time I update the emoji in the pack, I'll probably tackle that first.

Also, it'd be nice to add more emoji!  This will involve adding another source other than Joel's files somehow, but that shouldn't be too difficult.

If there's any emoji you find are missing, or if you see any problems with the implementation, please either drop me a line at joewoods@fastmail.com or leave an issue on the Github repository.

👋🏻
