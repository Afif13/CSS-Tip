---
layout: layouts/post.njk
title: A rainbow gradient animation
description: Use the new color interpolation to create an infinite rainbow gradient animation
date: 2023-01-31
tags: posts
---


Use the new color interpolation to easily create an infinite rainbow animation using CSS gradients 🌈

* One color declaration
* A simple animation


```css
html {
  background: 
    linear-gradient(90deg in hsl longer hue, red 0 50%) 0/200%;
  animation: r 6s linear infinite;
}
@keyframes r {
  to {background-position: 100%}
}
```


<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="qByJMxL" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/qByJMxL">
  rainbow gradient animation </a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>