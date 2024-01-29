---
layout: layouts/post.njk
title: A curved ribbon shape with hover effect
description: A simple ribbon shape with a fancy hover effect
date: 2024-01-29
tags: posts
---

Create a simple ribbon shape with a cool hover effect
* Only one element
* Optimized with CSS variables
* Powered by @property


{% image "./image.png", "Curved ribbon shape" %}

```css
@property --a {
  syntax: "<angle>";
  initial-value: 0deg;
  inherits: true;
}

.ribbon {
  --c: #60b0a7;
  --r: .8em;  
  --a:  0deg; /* this will get animated */
  --d: .5em;

  padding-inline: .3em;
  margin: calc(.5lh + var(--r)) calc(1.2lh + var(--d));
  background: var(--c);
  position: relative;
  transition: --a .6s;
}
.ribbon:hover {
  --a: 60deg; 
}
.ribbon:before,
.ribbon:after {
  content: "";
  position: absolute;
  width: calc(1lh + var(--d));
  height: calc(1.5lh + var(--r));
  border: solid var(--c);
  box-sizing: border-box;
  rotate: calc(var(--a) - 90deg);
}
.ribbon:before {
  left: 99%;
  top: 0;
  border-width: 1lh 1lh 0 0;
  border-radius: 0 999px 0 0;
  clip-path: polygon(calc(999px*cos(var(--a))) calc(1lh + var(--d) - 999px*sin(var(--a))),999px 100%,100% 100%,calc(50% + var(--d)/2) calc(100% - var(--r)),var(--d) 100%,0 100%, 0 calc(1lh + var(--d)));
  transform-origin: 0 calc(1lh + var(--d));
}
.ribbon:after {
  right: 99%;
  bottom: 0;
  border-width: 0 0 1lh 1lh;
  border-radius: 0 0 0 999px;
  clip-path: polygon(calc(100% - 999px*cos(var(--a))) calc(100% - 1lh - var(--d) + 999px*sin(var(--a))),-999px 0,0 0,calc(50% - var(--d)/2) var(--r),calc(100% - var(--d)) 0,100% 0, 100% calc(100% - 1lh - var(--d)));
  transform-origin: 100% calc(100% - 1lh - var(--d));
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="KKEZZev" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/KKEZZev">
  Fancy ribbon with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>