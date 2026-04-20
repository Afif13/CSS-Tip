---
layout: layouts/post.njk
title: Hand-Drawn Underline using border-shape
description: Add a fancy underline to your menu items using modern CSS
date: 2026-04-20
tags: posts
---

Use [the new `border-shape` property](/border-shape/) and transform the classic underline into hand-drawn lines! It works with a simple code, and you can easily generate the wavy shape using [my online generator](https://css-generators.com/wavy-divider/)

{% image "./image.png", "A CSS-only hand-drawn underline" %}

```css
ul {
  padding: 0 0 20px;
  border-bottom: 6px solid #fb8500;
  border-shape: shape(/* code from the generator */);
  clip-path: inset(0);
}
ul:after {
  content: "";
  position: absolute;
  position-anchor: --a;
  inset: anchor(outside) anchor(inside) 0;
  border-image: conic-gradient(#f2f2f2) 1/0 100vw/0 100vw; /* the color used here must match the background color */
  transition: .2s;
}
ul li a:is(:hover,[aria-current],:focus-visible) {
  anchor-name: --a;
}
ul:has(a:is(:hover,:focus-visible)) a:not(:hover,:focus-visible) {
  anchor-name: none;
}
```

`border-shape` is a Chrome-only feature for now. You will get a classic underline in the other browsers.

<p class="codepen" data-height="400" data-pen-title="Hand-Drawn Underline using border-shape" data-preview="true" data-default-tab="result" data-slug-hash="emdoVae" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/emdoVae">
  Hand-Drawn Underline using border-shape</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

To change the shape, select the border-only version and the bottom side from [the generator](https://css-generators.com/wavy-divider/), then adjust the other values like you want (granularity, size, and shape ID). The `padding-bottom` of the `ul` needs to be equal to the size value, and to control the line's thickness and color, simply adjust the `border` property.

{% image "./image1.png", "Overview of wavy shape generator" %}