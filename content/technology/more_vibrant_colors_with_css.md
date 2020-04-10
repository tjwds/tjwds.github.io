+++
title="More Vibrant Colors with CSS"
date=2020-04-10
+++

<style type="text/css">
.gradient-block {
    width: 100%;
    height: 10rem;
    padding: 0.5rem;
    background: violet;
}
.gradient-0 {
    background: linear-gradient(45deg, #f00 10%, #0f0, #00f 90%);
}
.gradient-1 {
    background: linear-gradient(45deg, color(srgb 1 0 0) 10%, color(srgb 0 1 0), color(srgb 0 0 1) 90%);
}
.gradient-2 {
    background: linear-gradient(45deg, color(display-p3 1 0 0) 10%, color(display-p3 0 1 0), color(display-p3 0 0 1) 90%);
}
.gradient-3 {
    background: linear-gradient(45deg, color(a98-rgb 1 0 0) 10%, color(a98-rgb 0 1 0), color(a98-rgb 0 0 1) 90%);
}
.gradient-4 {
    background: linear-gradient(45deg, color(prophoto-rgb 1 0 0) 10%, color(prophoto-rgb 0 1 0), color(prophoto-rgb 0 0 1) 90%);
}
.gradient-5 {
    background: linear-gradient(45deg, color(rec-2020 1 0 0) 10%, color(rec-2020 0 1 0), color(rec-2020 0 0 1) 90%);
}

.example-broken {
    background: violet;
    height: 2rem;
    width: 2rem;
    margin: 1rem;
    float: left;
    display: inline-block;
}

.less-vibrant-colors, .vibrant-colors {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    padding: 2rem 0;
}
.less-vibrant-colors {
    background: linear-gradient(rgb(0, 255, 204), rgb(0, 102, 204));
}
.vibrant-colors {
    background: violet;
    background: linear-gradient(color(display-p3 0 1 0.8), color(display-p3 0 0.4 0.8));
}

.less-vibrant-colors--text, .vibrant-colors--text {
    color: violet;
    text-align: center;
    font-size: 3rem;
    font-weight: bold;
}
.less-vibrant-colors--one {
    color: rgb(255, 255, 0);
}
.vibrant-colors--one {
    color: color(display-p3 1 1 0);
}
.less-vibrant-colors--two {
    font-size: 5rem;
    color: rgb(255, 182.325, 0);
}
.vibrant-colors--two {
    font-size: 5rem;
    color: color(display-p3 1 0.715 0);
}

.vibrant-colors--text {
    color: violet;
    text-align: center;
    font-size: 3rem;
    font-weight: bold;
}
.vibrant-colors--one {
    color: color(display-p3 1 1 0);
}
.vibrant-colors--two {
    font-size: 5rem;
    color: color(display-p3 1 0.715 0);
}

.lyft-one {
    background-color: #ff00bf;
}
.lyft-two {
    background-color: color(display-p3 1 0.22 0.808)
}
</style>

Soon the colors that you see on webpages are going to be a lot more vibrant.  Here's an example; the only problem is, at time of writing, the only browsers that support this example are Safari on iOS and macOS:

<div class="gradient-block gradient-0">rgb hex values (srgb color space)</div>
<div class="gradient-block gradient-2">display-p3</div>

<div>
<div class="example-broken"></div>

Note:  if, at any point, you see an example that has a "violet" background color like the element to the left, it means that your browser doesn't support rendering the example.
</div>

You've been seeing these colors for a while now.  Film and photography use this color space (or one close to it) to represent vivid colors that are closer to real life.  This gives color that "HDR" feel. Here's an inexact comparison of the available colors in each color gamut:  display-p3 gives you access to not only a wider range of colors, but the more intense colors that sRGB is lacking:

{{ figure(
    title="DCI-P3 D65 v CIExy1931 sRGB"
    src="/images/color_gamut.jpg"
    content="DCI-P3 D65 v CIExy1931 sRGB.  I say 'inexact' because this is a hastily-done photoshop mashup of two files: <a href='https://commons.wikimedia.org/wiki/File:CIExy1931_sRGB_gamut_D65.png'>one for sRGB</a> and <a href='https://commons.wikimedia.org/wiki/File:DCI-P3_D65.svg'>one for display-p3</a>. This image is likewise licensed under the <a href='https://creativecommons.org/licenses/by-sa/3.0/deed.en'>Creative Commons Attribution-Share Alike 3.0 Unported</a> license."
) }}

Some web browsers are already able to render images in alternate color spaces — webkit has some great examples [on this page](https://webkit.org/blog-files/color-gamut/).  But now we have this capability for the rest of the page!  WebKit has [a blog post](https://webkit.org/blog/10042/wide-gamut-color-in-css-with-display-p3/) that goes into detail about the way this works in Safari as expressed in CSS and how it works in the developer tools… but they didn't really show any examples of what it looks like and how it might be used in the near future.

So what does this mean for web design? Perhaps it means that designers will start including two colors: their first preference and a less vibrant fallback.

<div class="less-vibrant-colors">
<div class="less-vibrant-colors--text less-vibrant-colors--one">less vibrant</div>
<div class="less-vibrant-colors--text less-vibrant-colors--two">colors</div>
</div>
<div class="vibrant-colors">
<div class="vibrant-colors--text vibrant-colors--one">more vibrant</div>
<div class="vibrant-colors--text vibrant-colors--two">colors</div>
</div>

Pantone's color of the year for 2013, Emerald 17-5641, [is outside of sRGB](hhttps://dot-color.com/2012/12/11/color-of-the-year-for-2013-falls-outside-srgb-gamut/), but now you can use it in Safari… that is, if you can get ahold of its relative display-p3 values. I couldn't.

Maybe Lyft could dive even further into magenta:

<div class="gradient-block lyft-one">Lyft pink hex codes from Lyft's March 2018 brand guidelines</div>
<div class="gradient-block lyft-two">A more intense pink in display-p3 (or the css 'violet' value if your browser doesn't support display-p3… which is a little too similar to this example, sorry!!)</div>

The [CSS Color Module Level 4 working draft](https://www.w3.org/TR/css-color-4/#predefined) defines a `color` function which allows you to choose your color space.  Here's one example from this page:

```css
.less-vibrant-colors--one {
    color: rgb(255, 255, 0);
}
.vibrant-colors--one {
    color: color(display-p3 1 1 0);
}
```

Other color spaces mentioned by the draft, in addition to srgb and display-p3, are a98-rgb, prophoto-rgb and rec-2020.

<div class="gradient-block gradient-0">rgb hex values (srgb color space)</div>
<div class="gradient-block gradient-1">srgb (just a different way of expressing the values above!)</div>
<div class="gradient-block gradient-2">display-p3</div>
<div class="gradient-block gradient-3">a98-rgb</div>
<div class="gradient-block gradient-4">prophoto-rgb</div>
<div class="gradient-block gradient-5">rec-2020</div>

At time of writing, display-p3 is the only alternate color space implemented by any browser.
