+++
title="Meta Content with Zola"
date=2020-04-11
description="I added meta tags and an RSS feed to my site today."
+++

I added meta tags and an RSS feed to my site today.

<!-- more -->

## RSS

"RSS, you say?" I hear you ask.  Yes, RSS.  I've very recently started subscribing to RSS feeds for software releases, so naturally my site needs <a href="https://blog.joewoods.dev/rss.xml">a feed</a> too.

Adding this in Zola is really straight-forward:  first, tell Zola to generate RSS in your `config.toml` file:

```toml
# adds /rss.xml
generate_rss = true
```

You should also add a reference to it the `head` of your templates — if you're like me and everything extends the same index template, this is simple:

```html
<meta property="og:url" content="{{config.base_url | safe}}/{{current_path | safe}}" />
```

## Meta, Open Graph, Twitter card

You'll see a lot of bias in my implementation here:  I don't define a site-wide picture (yet?) because I can't think of one that I want to add right now, and I've skipped some meta information that other people might want to add, like your Facebook Brand Id.  I'm also duplicating the description tag for each metadata collection type, mostly out of laziness… it's not strictly necessary to overwrite the meta description with, say, the `og:description` property, but I figure it doesn't hurt in case someone's written a really bizarre meta tag parser.

So, generally, you should use what I'm doing on my site as more of a general idea of how to accomplish this in Zola, without copying what I've done exactly.  Do your own research as to what meta tags you want to include.

In my index template, I have a big block of meta tags that are separated into two sections:  things which will be true for every page on the site, and things that should be overwritten in specific articles.  The latter category has been placed in a `meta_content` block:

```html
<meta name="twitter:card" content="summary">
<meta name="twitter:site" content="@tjwds">
<meta name="twitter:creator" content="@tjwds">
<meta property="og:type" content="article" />
<meta property="og:url" content="{{config.base_url | safe}}/{{current_path | safe}}" />
<meta property="og:site_name" content="Joe Woods — Blog" />

{% block meta_content %}
<title>Joe Woods – Blog</title>
<meta name="twitter:title" content="Joe Woods — Blog">
<meta property="og:title" content="Joe Woods — Blog" />
{% endblock meta_content %}
```

Which I then programmatically overwrite on my `page` template:

```html
{% block meta_content %}
    {% if page.title %}
    <meta name="twitter:title" content="{{page.title}} — Joe Woods">
    <meta property="og:title" content="{{page.title}} — Joe Woods" />
    {% else %}
    <meta name="twitter:title" content="Joe Woods — Blog">
    <meta property="og:title" content="Joe Woods — Blog" />
    {% endif %}
    {% if page.description %}
    <meta name="description" content="{{ page.description | safe }}" />
    <meta name="twitter:description" content="{{ page.description | safe }}">
    <meta property="og:description" content="{{ page.description | safe }}" />
    {% endif %}
{% endblock meta_content %}
```

"What sort of article isn't going to have a title??" I hear you interject.  I don't know!  But, you know, better safe than sorry — it's better, in my opinion, to make the case for this now, as opposed to forgetting to fix it later.  Say I wanted to move off of blog.joewoods.dev — it's unlikely that I would, but who knows what will happen years down the line.  If I had hard-coded that value instead of using `{{config.base_url | safe}}`, I probably would have forgotten to update it there, and my blog would be shouting wrong information into the void until the end of time.
