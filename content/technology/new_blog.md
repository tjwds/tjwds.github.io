+++
title="New Blog"
date=2020-01-19
teaser="I have a new blog!  You can find the source [on Github](https://github.com/tjwds/tjwds.github.io)."
+++

I have a new blog!  You can find the source [on Github](https://github.com/tjwds/tjwds.github.io).
<!-- more -->

## Tech Stack

### Zola

The pages are written and stored as markdown files, which are built with [Zola](https://www.getzola.org/).  Zola is pretty great — it does exactly what's on the tin, and though it's nearly impossible to search for documentation for it due to an unfortunate collision with another brand's name, everything about the way Zola projects are created is pretty intuitive.  It seems like there's not a lot of folks who are currently using it because there really aren't a lot of tutorials that aren't official documentation on random folks' blogs, like you tend to find with other platforms.

Nevertheless, self-discovery with the templating engine that Zola uses, [Tera](https://tera.netlify.com), is fairly straight-forward if you're used to any other templating engine.  Honestly, if you've used one, you've used them all at this point.

### Travis CI and Github Pages

This is sort of silly, but I didn't really give a lot of thought to where I was going to host this blog, or even how it was going to be built.  I sort of arrived at the "JAM Stack" on accident, just because so many things about it are abstracted away to a point where I don't really have to think about it.  I really enjoy the CI deployment structure of other projects I've worked on, where I don't even need to push a button after committing to the publish branch — it just does it for me.

Zola has some pretty good documentation for Github Pages and Travis CI, so I decided to give that a shot.  At time of writing, the Zola documentation doesn't mention that Ubuntu Xenial (16.04, the Travis CI default) fails to build Zola for some reason or other, so I've just added the line `dist: bionic` to my config to build on 18.04 instead.  I also had to add a CNAME file to my static folder to make sure I didn't destroy my custom subdomain with every push, which was a frustrating problem to try to find an answer to.

Github Pages works, but it doesn't have a great user experience, in my opinion.  It feels like the whole feature is just a hack that was laid on top of Github that an ecosystem has slowly evolved around… but the feature on Github hasn't really been updated to match.

For instance, why on earth does my repo name need to be `username.github.io` when I'm using my own domain?  And now, even though I'm a Github Pro user, if I want to add another Github Pages project, I'll need to create a new organization.  That's not fun.

With that being said, I'm hoping that the decision to not host anything myself here will mean that I can not worry about whether or not this site is up!

## Features

### Typography

Zola has built-in SCSS support.  I wanted to make sure that I wasn't spending a lot of time styling this blog, but I also wanted to get it _right_, you know?

Everything is measured in ems.  This is so our breakout images and code snippets (more detail below) don't break if the browser has increased the font size.  It's also way more of a breeze to handle the margin and padding for any individual elements when it's in portions of an em!

### Figure template

One of the first things I did was to create a figure shortcode for my articles.  I'm a hobbyist photographer and wanted to be sure I was happy with the way images are displayed here, so I created a shortcode template:

```html
<figure {% if class %}class="{{class}}"{% endif %}{% if title %}alt="{{title}}" title="{{title}}"{% else %}alt=""{% endif %}>
    <img src={{src}} />
    {% if content %}
    <figcaption>
        {{ content | safe }}
    </figcaption>
    {% endif %}
</figure>

```

Essentially, everything is optional but the image `src`.  The shortcode is invoked as follows anywhere, be it in an html template or in markdown:

<!-- I couldn't get the raw template to work, so I've included a zero width space as an extremely bad hack in between the two curly braces starting this figure. --->
```markdown
{​{ figure(
    title="Fog on Mountain"
    src="https://images.unsplash.com/photo-1497216429614-5bd7dbd9fc48?ixlib=rb-1.2.1&auto=format&fit=crop&w=2252&q=80"
    content="Photo by <a href='https://unsplash.com/photos/tLDeO8lTgII'>Joe Woods on Unsplash</a>"
) }}
```

And here's the result!

{{ figure(
    title="Fog on Mountain"
    src="https://images.unsplash.com/photo-1497216429614-5bd7dbd9fc48?ixlib=rb-1.2.1&auto=format&fit=crop&w=2252&q=80"
    content="Photo by <a href='https://unsplash.com/photos/tLDeO8lTgII'>Joe Woods on Unsplash</a>"
) }}

### Code snippets

Zola has [built-in support for code syntax highlighting](https://www.getzola.org/documentation/content/syntax-highlighting/), which is very convenient.  I've kept everything as provided out of the box (for now?) because I find whichever color theme I'm now using to be pretty good!  I've added a little bit of padding to the text, as well as applied some more space between each line and letter form to make things a little more legible (for me, at least).  You'll also notice that on wider monitors, the code snippets will take up a little more space than the width of our text column, but will collapse in with a horizontal, scrolling overflow if we don't have enough room.

Here's an example:

```javascript
for (var i = 1; i <= 100; i++) {
    if (!(i % 15)) {
        console.log("FizzBuzz");
    }
    else if (!(i % 3)) {
        console.log("Fizz");
    }
    else if (!(i % 5)) {
        console.log("Buzz");
    }
    else {
        console.log(i);
    }
}
"234567890123456789 1234567890123456789 1234567890123456789 123456789012345678";
```

## Conclusion

I've been writing more lately, so hopefully being able to easily and quickly deploy new blog posts will mean that I'll share more!
