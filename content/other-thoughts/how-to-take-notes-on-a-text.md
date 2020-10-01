+++
title="How to Take Notes on a Text"
date=2020-09-30
+++

I am a computer programmer who received his master's in English.  I admit that this means that I don't necessarily have the best grasp on some concepts that other engineers might consider basic knowledge, but what I lack there I sincerely believe I make up for in tools I've built for myself to be able to research and communicate the best I ever can.

We all have systems for how we interact with everything, be they formal and rarely-changing, or informal and amorphous.  One of the most important decisions you make whenever you do anything is whether or not you are going to follow the checklist.  Almost always, this decision is automatic, and you don't even realize that you're making it.  But you have a choice every time.

Unless you're a pilot or something.  You'll still have a choice as to whether or not to follow the checklist before taking off, but you almost certainly should.

So:  how do you build and use a formal set of constraints for taking notes?  For me, this came about from practice — trying things out and seeing if they'd stick, and borrowing ideas from others when I thought they'd make sense for my system.  This document represents the sum of these efforts — the total combination of work that I've done to improve this specific facet of the work that I do both for my career and in my personal life.

I hope, by showing off the way I organize my research notes, that you can do the same thing:  take what you like, try it out in whatever way you want, use it, or just let it add a few more ideas to the pile that you can draw from later down the road.

## Why this system

Most of the time, I will only read something once, and anything that sticks out goes into my notes document, which will then be the thing that I will consult in the future.  Lately, I've almost entirely been applying this system to books that are either directly about or tangentially related to programming, but in grad school, I used this system for articles and for fiction as well.

In grad school, I probably turned out about two papers a week.  In life, now, I probably make more flashcards for myself than I really should.

For both of these contexts, it's good to have an easy repository of knowledge.  By having everything in one place, in an actionable document, I could, say, write an essay on a text by skimming the points I made to myself, directly quoting from the source just by copying and pasting the quote I had transcribed earlier.  When reading a technical manual or treatise on a subject, it's great to just have one source that I can then pass through and make sure I convert the important things that I want to get from the text into permanent knowledge.

But above all else, creativity comes from constraint.  By setting myself up to have a system where close reading requires a computer, where I _must_ read actively and transcribe, I will always be doing my best work when reading.

Unless I'm reading exclusively for pleasure, then I don't use this system at all.

## Other rules

* *Don't confuse your page numbers.* The book page is the page number that appears typeset on the page itself, the *pdf page* is the page of the PDF that we're currently on.  For example, you may have a PDF that is a scanned article from the middle of the textbook — you must cite, say, book page number 200 when transcribing a quote, but it's often easier to write down the book page when writing down something that will help you find something in the text at a later time.
* *Just write it in markdown.*  You should learn markdown — it's everywhere.
* *Make it accessible.*  You should be able to edit your notes from anywhere, at any time.  Unless you don't have a phone or a computer in front of you, that is, but come on, that's so rare, now-a-days.
* *Back up your work.*  There's no point in going through all this trouble if you can't come back to your beautiful notes five, twenty, or 100 years from now.  Only keeping one copy of your notes on Google Docs is not a good backup strategy!  In fact, if you go all-in on this system, you may end up with a document with a large number of quote from outside sources that could trip some content filter in the shadows of any proprietary platform you use and cause your notes to suddenly disappear one day without warning or explanation.  So:  back up your notes!
* *Make it your own!*  Take what I've written here and make it make sense for you; remix it and fit it into your life as much as you want.  Definitely don't take any of this as law.

## The system

Each document is formatted in the following way:

* The h1 is the title of the book.  Below it goes an MLA citation.  There may also be additional thoughts, TODOs, or other information about the text in the topmost section.
* Each chapter with notes gets its own h2.  (Sub-sections are likewise headed the next heading down.)
* Each independent thought is an item in an unordered list. The first characters of a thought indicate:
    * .: this is my commentary
    * page number: direct quote from the source when wrapped in quotes, paraphrased information that would still require a citation if not.
        * Must _always_ be the book page number for the sake of citations!
        * Page number may be a span of numbers, or roman numerals (or maybe even a span of roman numerals)
        * I try to directly quote (wrap in quotation marks) as often as possible, because it means that quoting directly from the source is _absurdly_ easy — I just lift the quote from my notes instead!
            * This saved my butt countless times in college, especially.
    * ?: a question I have.  Answers may be indented.
    * !: I need to make a flashcard for this.
    * !+: I made a flashcard for this.
    * !-: I marked that was going to make a flashcard for this, but didn't end up doing so.
    * !!! This is really cool.
* Some tags _may_ be combined.
* The last non-heading line of a file will almost certainly be a declaration of the place I stopped in a document, i.e. "stopped on pdf page 56."
    * It's really important to note here whether or not we're referring to the PDF page or the book page with this number!

## A brief example

```
# _Excession_ by Iain M. Banks

Banks, Iain M. _Excession_. New York, NY: Bantam Books, 1998.

## Prologue

* 1 "That light came from a line, not a point in the sky, because the place
where Dajeil Gelian lived was not a planet."
    * . This… doesn't make a lot of sense.  Almost all of Banks' future-fantasy
    ideas make sense.  This one does not.
* 2 "The woman heard the landward gate-bell tinkle, but already knew that she
had a visitor because the black bird Gravious had told her […]"
    * . Banks really has a thing for birds telling you things — see also
    _Feersum Endjinn_, released just two years before.
    * ? Has anyone written about birds in Banks novels?

Stopped on page 4
```
