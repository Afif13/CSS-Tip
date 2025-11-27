---
layout: layouts/post.njk
title: Direction-Aware CSS Shapes
description: A few lines of code to make any CSS shape adjust according to the direction of the text
date: 2025-11-27
tags: posts
---

Building on [the previous idea](/arrow/), here is a more generic piece of code to make any CSS shape direction-aware. It relies on a few lines of well-supported CSS code.

{% image "./image.png", "Direct-aware CSS-only shapes" %}


```css
.shape {
  position: relative;
  overflow: hidden;
}
.shape:before,
.shape:after {
  content: "";
  position: absolute;
  width: 100%;
  inset-block: 0;
  translate: 100%;
  /* Build your shape using whatever you want
    clip-path: ...;
    mask: ...;
    background: url(...);
    content: "👉";
  */
}
.shape:before {
  inset-inline-end: 100%;
}
.shape:after {
  inset-inline-start: 100%;
  scale: -1 1;
}
```

Here are a few examples of shapes, mostly taken from [css-shape.com](https://css-shape.com/). Adjust the direction and see how they behave:

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="xbVjbzY" data-pen-title="Direction-aware CSS shapes" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/xbVjbzY">
  Direction-aware CSS shapes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

## How Does It Work?

First, we create the shape using both pseudo-elements, which results in the same shape appearing twice.

```css
.shape {
  position: relative;
}
.shape:before,
.shape:after {
  content: "";
  position: absolute;
  width: 100%;
  inset-block: 0;
  clip-path: polygon(0 0,100% 50%,0 100%);
}
```

Then, we place one pseudo-element with `inset-inline-end: 100%` and the other with `inset-inline-start: 100%`. Depending on the direction, they will get mapped to either `left: 100%` or `right: 100%`. We invert one of the shapes using `scale: -1 1`.

{% image "./image1.png", "Overview of the shapes position" %}

Both shapes are outside the element boundary, and they swap their position according to the direction. We translate both of them to the right using `translate: 100%` so that only one shape is inside the element boundary. 

{% image "./image2.png", "Showing one css shape at once" %}

We hide the overflow, and it's done!