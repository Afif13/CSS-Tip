---
layout: layouts/post.njk
title: Responsive ASCII Arts using text-fit
description: Thanks to a new CSS property, it's now easy to create responsive ASCII art
date: 2026-07-21
tags: posts
---

Using the new `text-fit` property, you can easily make your ASCII art responsive with a simple code!

{% image "./image.png", "ASCII art of a dragon" %}


```css
.box {
  white-space: pre; /* preserve the white spaces */
  font-size: 30px; /* use a big font-size */
  text-fit: shrink; /* allow the font-size to shrink when the box is small */
}
```

Resize the box in the demo below and see the magic in play!

⚠️ (Chromium only for now) ⚠️

<p class="codepen" data-height="600" data-pen-title="Responsive ascii art" data-preview="true" data-default-tab="result" data-slug-hash="dPNjOoo" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dPNjOoo">
  Responsive ascii art</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

<small>Art taken from: [https://emojicombos.com/ascii-art](https://emojicombos.com/ascii-art) </small>

As its name suggests, the `text-fit` property allows the text to fit the container by scaling the font size. We generally reach for the `grow` value to fill that little space at the end of each line. `shrink` is more useful when you want to scale down an overflowing text.

{% image "./image1.png", "fitting the text on each line" %}

We can have the same scaling factor for all the lines (it's the default behavior). It keeps the font size the same for all lines, but we still have blank spaces. Useful for responsive ASCII arts.

```css
.box {
  text-fit: [shrink | grow] consistent; /* consistent can be omitted */
}
```

Or use a different scaling factor per line. All the spaces are filled, and we have a different font-size per line.

```css
.box {
  text-fit: [shrink | grow] per-line; 
  /* OR  */
  text-fit: [shrink | grow] per-line-all; /* to include the last line */ 
}
```

Here is a demo where you can switch between the different values. Resize the box to better see the effect of each one:

<p class="codepen" data-height="500" data-pen-title="testing text-fit" data-preview="true" data-default-tab="result" data-slug-hash="WbRKEQr" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/WbRKEQr">
  testing text-fit</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script> 