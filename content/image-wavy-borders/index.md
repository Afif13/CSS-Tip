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
  --s: 20px;  /* control the size of the wave */
  --w: 300px; /* preferred image width */
  
  width: round(var(--w),4*var(--s)); 
  aspect-ratio: 1;
  padding: var(--s);
  border: var(--s) solid #0000;
  box-sizing: border-box;
  border-radius: calc(3.5*var(--s));
  mask: 
    radial-gradient(calc(sqrt(2)*var(--s)),#000 calc(100% - 1px),#0000),
    conic-gradient(#000 0 0) content-box,
    radial-gradient(calc(sqrt(2)*var(--s)),#0000 100%,#000 calc(100% + 1px)) 
     var(--s) var(--s) padding-box;
  mask-size: calc(var(--s)*4) calc(var(--s)*4);
}
```


<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="EaYedaY" data-pen-title="Images inside wavy boxes" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/EaYedaY">
  Images inside wavy boxes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

