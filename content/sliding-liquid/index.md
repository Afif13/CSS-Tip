---
layout: layouts/post.njk
title: 'Sliding "Liquid Oozing" Reveal Effect'
description: "A fancy reveal animation powered by clip-path: shape"
date: 2026-04-02
tags: posts
---

Create a fancy reveal animation with a "liquid oozing" effect using `shape()`. Code generated using [my wavy divider generator](https://css-generators.com/wavy-divider/)

{% image "./image.png", "CSS-only Sliding liquid effect" %}

```css
html:after {
  content: "";
  position: fixed;
  inset: 0;
  background: #219ebc;
  animation: reveal 6s 1.5s both;
}
@keyframes reveal {
  0% {
    clip-path: shape(/* code from the generator */);
  }
  to {
    translate: 0 110%;
    clip-path: shape(/* code from the generator */);
  }
}
```

<p class="codepen" data-height="600" data-pen-title="Sliding reveal animation" data-preview="true" data-default-tab="result" data-slug-hash="OPRZBxY" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/OPRZBxY">
  Sliding reveal animation</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>


First, select the top configuration, set the granularity, and generate a shape (the shape ID). Then, you adjust the size of the wave at `0%` then at `100%`  to get the code for both shapes.

{% image "./image1.png", "Showing both shapes from the generator" %}

Having the same granularity and shape ID will allow the browser to have a smooth transition between both shapes and create that fancy effect.