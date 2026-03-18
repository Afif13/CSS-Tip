---
layout: layouts/post.njk
title: Add a Wobbling Animation to your Images
description: Create an infinite fancy animation using clip-path and shape()
date: 2026-03-18
tags: posts
---

Use `shape()` and my [fancy frames generator](https://css-generators.com/fancy-frame/) to create an infinite wobbling animation for images or any elements. It's a single-element implementation with simple code.


{% image "./image.png", "CSS-only woobling effect" %}

```css
img {
  animation: shape 4s linear infinite;
}
@keyframes shape {
  0%,to {clip-path: shape(/* from the generator */)}
  33.3% {clip-path: shape(/* from the generator */)}
  66.6% {clip-path: shape(/* from the generator */)}
}
```

All you have to do is fix the granularity, then generate three different shapes. The same granularity will ensure the same number of curves/points, allowing the browser to have a smooth transition between the shapes.

<p class="codepen" data-height="450" data-pen-title="Untitled" data-preview="true" data-default-tab="result" data-slug-hash="zxKzrKe" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zxKzrKe">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>
