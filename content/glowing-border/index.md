---
layout: layouts/post.njk
title: Glowing border animation with a smooth stop
description: Add a fancy border animation on hover that stops smoothly on mouseout
date: 2024-12-03
tags: posts
---

Add a glowing border animation around your image (or any element) with a few lines of code. The cool part? It's an infinite animation on hover that stops smoothly when the mouse leaves the element!

Single element implementation powered by modern CSS (`@property`, CSS Mask, Math functions, etc).

{% image "./image.png", "CSS-only glowing border effect" %}

```css
@property --a {
  syntax: "<angle>";
  inherits: false;
  initial-value: 0deg; 
}
@property --i {
  syntax: "<number>";
  inherits: false;
  initial-value: 0; 
}
img {
  border: 5px solid #ccc;
  padding: 10px; /* control the gap */
  mask: 
    conic-gradient(#000 0 0) content-box,
    linear-gradient(calc(mod(var(--a),180deg)*var(--i) + 45deg),
      #0000 30%,#000 40% 60%,#0000 70%) subtract,
    conic-gradient(#000 0 0) padding-box;
  transition: --i .5s,--a 0s .5s;
}
img:hover {
  --i: 1;
  --a: 15turn; 
  transition: --i 0s,--a 30s linear;
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="dPbomxP" data-pen-title="Glowing border animation on hover with a smooth stop" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dPbomxP">
  Glowing border animation on hover with a smooth stop</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>