---
layout: layouts/post.njk
title: A fancy frame with wavy borders (wavy box)
description: Place your image inside a wavy box using modern CSS
date: 2024-01-23
tags: posts
---

Place your image inside a [wavy box](https://css-shape.com/wavy-box/) using a few lines of code
* Only one element (the `<img>` tag)
* No pseudo-elements
* Optimized with CSS Variables
* Works with gradient coloration

{% image "./image.png", "CSS-only images with wavy borders on all the sides" %}

```css
img {
  --s: 80px;  /* control the size of the wave */
  --w: 300px; /* preferred image width */
  
  width: round(var(--w),var(--s)); 
  aspect-ratio: 1;
  padding: calc(var(--s)/2);
  box-sizing: border-box;
  border-radius: calc(.85*var(--s));
  --_r:calc(sqrt(2)*var(--s)/4),#000;
  --_g:conic-gradient(#000 0 0) no-repeat;
  mask: 
    radial-gradient(var(--_r) calc(100% - 1px),#0000) 
     0 0/var(--s) var(--s),
    var(--_g) content-box,var(--_g) subtract 
     50%/calc(100% - var(--s)/2) calc(100% - var(--s)/2),
    radial-gradient(var(--_r) 100%,#0000 calc(100% + 1px)) 
     calc(var(--s)/2) calc(var(--s)/2)/var(--s) var(--s);
}
```


<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="EaYedaY" data-pen-title="Images inside wavy boxes" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/EaYedaY">
  Images inside wavy boxes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

