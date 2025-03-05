---
layout: layouts/post.njk
title: Get the value of an input range (without JavaScript)
description: Use modern features to get the value of an input range using only CSS
date: 2025-03-05
tags: posts
---

A few lines of code and you have a CSS-only way to read the value of an input range slider. Powered by Scroll-driven animations, `attr()`, and `@property`. No more JavaScript!

⚠️ Chrome-only for now ⚠️

```css
@property --val {
  syntax: "<number>";
  inherits: true;
  initial-value: 0; 
}
input[type="range"] {
  timeline-scope: --val;
  animation: --val linear both;
  animation-timeline: --val;
  animation-range: entry 100% exit 0%;
  overflow: hidden;
  /* --val will automatically update when you interact with the range slider */
}
@keyframes --val {
  0% {--val: attr(max type(<number>),100)}
  to {--val: attr(min type(<number>),1  )}
}
input[type="range"]::-webkit-slider-thumb{
  view-timeline: --val inline;
}
```

The value is scoped to the input element, if you want to make it available everywhere on the page check this: [Update CSS variables using range slider](https://css-tip.com/css-variables-range-slider/)

Here is an example of a star rating component built using the above code:

<p class="codepen" data-height="350" data-default-tab="result" data-slug-hash="dPyWvqg" data-pen-title="Star rating using scroll-driven animations" data-preview="true" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dPyWvqg">
  Star rating using scroll-driven animations</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Another crazy idea with a wavy range slider.

<p class="codepen" data-height="351" data-default-tab="result" data-slug-hash="xbxVxVQ" data-pen-title="Single-element wavy range slider" data-preview="true" data-user="t_afif" style="height: 351px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/xbxVxVQ">
  Single-element wavy range slider</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>
