+++
title="Underengineered, privacy-oriented web analytics"
date=2020-05-03
description="If you already have the tools, you can see what's going on on your site 'for free.'"
+++

After circulating a blog post I wrote, I realized I had three questions:

* How do I track views on a Github Pages blog in a way that respects my users' privacy?
* What's a cheap option for web analytics that isn't Google Analytics?
* What on earth am I doing?  What do all of these words mean?

<!-- more -->

But really, why _doesn't_ Github offer some way of tracking page views?  I'm sure you have this data, Microsoft, and it seems like more and more folks are using Pages…

But anyway, I did what any sane software engineer would do and _way_ overthought a web analytics solution for myself. During this process, I sketched out what my ideal paid web analytics service would look like, and I briefly toyed with the idea of setting up some monstrosity of an AWS service to do exactly what I wanted to do.

But, in the end, I landed on a tried and true technology:  I implemented a tracking pixel.

I wouldn't consider this a guide for how to do this yourself, per se.  Just consider it a loose collection of ideas that you might be able to use for yourself.

## Implementation

So — how to implement a tracking pixel?  Well, I already have a few DigitalOcean droplets that I can easily slamjam some stuff on, so let's just… do it.

Our directory structure will look something like this…

```
joe/
├── track/
│   ├── blog/
|   │   └── track.gif
│   └── index.html
└── track_logs/
    └── track-access.log
```

And we can go ahead and set up the nginx conf to reflect that…

```conf
server {
    server_name track.joewoods.dev;

    location / {
        root /home/joe/track;
    }

    access_log /home/joe/track_logs/track-access.log;

    # Cert stuff automanaged by certbot got inserted here
}
```

I found an [_extremely_ cool repository of the smallest possible files of many types](https://github.com/mathiasbynens/small.git) — I went with the transparent gif.  It's 42 bytes.

Adding a new property is as easy as copying the pixel to a new directory, which you can then filter in your logs.

## Analysis

So now that we have a file of all of our visits, we can run `tail -f track_access.log` and real-time visitor logs.

```log
π.257.420.-1 - - [03/May/2020:13:35:25 +0000] "GET /blog/track.gif HTTP/1.1" 304 0 "https://blog.joewoods.dev/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:76.0) Gecko/20100101 Firefox/76.0"
```

I'm sure I'll end up writing some quick scripts if I want to see this visualized in any way, but as of right now, I haven't gotten there yet.  Or I could end up overthinking that too and use Databricks…
