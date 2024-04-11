---
layout: layouts/post.njk
title: CSS-Only pixelated cut corners
description: A few lines of code to create a fancy cut effect using mask
date: 2024-04-11
tags: posts
---

Use modern CSS to cut the corner of an image with a pixelated effect.
* Only one element (the `<img>` tag)
* Only 4 properties
* Optimized with CSS variables


{% image "./image.png", "A Rhombus shape with rounded corners" %}

```css
img {
  --n: 5;     /* the granularity */
  --s: 12px;  /* control the pixel size */
  --w: 280px; /* the image size */
  
  width: calc(round(var(--w),var(--s)) + var(--s)/2);
  aspect-ratio: 1;
  --_m:#0000 calc((var(--s)*(var(--n) + .5))/sqrt(2)),
       #000 0 calc(100% - (var(--s)*(var(--n) + .5))/sqrt(2)),
       #0000 0;
  clip-path: polygon(
    50% calc(var(--s)*var(--n) - 50%),
    calc(150% - var(--s)*var(--n)) 50%,
    50% calc(150% - var(--s)*var(--n)),
    calc(var(--s)*var(--n) - 50%) 50%);
  mask:
    repeating-conic-gradient(#0000 0 25%,#000 0 50%) 
     0 0/var(--s) var(--s),
    linear-gradient(-45deg,var(--_m)) intersect,
    linear-gradient( 45deg,var(--_m));
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="NWmzxQj" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/NWmzxQj">
  CSS-only pixelated cut corner</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


