---
layout: layouts/post.njk
title: An infinite number of borders around images
description: A border-image trick to add as many number of borders as you want
date: 2024-01-31
tags: posts
---

Use the magic `border-image` and add as many borders as you want to your images for a fancy decoration 
* No extra elements & No pseudo-elements
* Only one gradient
* Optimized with CSS variables


{% image "./image.png", "images with infinite borders" %}

```css
img {
  --s: 200px; /* image size */
  --b: 14px;  /* control the border thickness */
  --n: 5;     /* number of borders */
  --c: #774F38;
  
  width: var(--s);
  --_p:calc(var(--b)*var(--n));
  --_d:calc(var(--s)/(2*var(--n)) + var(--b));
  padding: var(--_p);
  border-radius: calc(var(--_p) + var(--b)/4);
  border-image:
    repeating-radial-gradient(
       var(--c) 0,#0000 2px calc(var(--_d)/2 - 2px),
       var(--c) calc(var(--_d)/2) var(--_d))
    49.8%/var(--_p);
  clip-path: inset(0 round var(--_p))
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="JjzpwyL" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/JjzpwyL">
  CSS only Infinite borders ∞</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>