---
layout: layouts/post.njk
title: Overlay reveal animation for your image
description: a fancy reveal animation using only one element
date: 2023-11-30
tags: posts
---

Add a reveal animation to your image with a simple code
* No extra element (only the image tag)
* No pseudo-elements
* Optimized with CSS Variables


{% image "./image.png", "CSS-only overlay reveal animation" %}

```css
@property --h { 
  syntax: "<length>";
  initial-value: 0px;
  inherits: true;
}
@property --e { 
  syntax: "<length>";
  initial-value: 0px;
  inherits: true;
}

img {
  --w: 200px; /* image size */
  --b: 12px;  /* control the overlay size (it will be w + b)*/
  --g: 15px;  /* the gap between the overlay and the image on hover */
  --c: #F56991;
  
  width: var(--w);
  aspect-ratio: 1;
  object-fit: cover;
  object-position: right;
  padding-inline: clamp(0px,var(--h),var(--w)) 0;
  box-sizing: border-box;
  background: var(--c);
  box-shadow: calc(var(--h) - var(--w) - var(--b) + var(--e)) 0 0 var(--b) var(--c);
  --h: calc(var(--w) + var(--b));
  --e: 0px;
  transition: --h .3s .3s linear,--e .3s linear;
}
img:hover {
  --h: calc(-1*var(--g));
  --e: calc(var(--w) + var(--b) + var(--g));
  transition: --h .4s linear,--e .3s .4s;
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="rNPZZbK" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/rNPZZbK">
  Sliding reveal effect for image II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Another version with a simplier animation

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="KKJxXKZ" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/KKJxXKZ">
  Sliding reveal effect for image</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>