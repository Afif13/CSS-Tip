---
layout: layouts/post.njk
title: Fix your images with an adhesive tape
description: A fancy effect using only the image element and a few lines of code
date: 2024-01-08
tags: posts
---

Don't let your images fall. Stick them with some adhesive tape! A CSS-only solution using a single element.
* Durable fixation & easy to remove
* Pre-cut adhesive tape
* Environment friendly ♻️


{% image "./image.png", "images with adhesive tape" %}

```css
img {
  --w: 280px; /* image width */
  --r: 1;     /* image ratio */
  /* control the tape dimension (adjust to understand) */
  --l: 45px;
  --s: 20px; 
  
  --_d:calc(var(--s) + var(--l));
  width: var(--w);
  padding: calc(var(--_d)/2);
  box-sizing: border-box;
  aspect-ratio: var(--r);
  object-fit: cover;
  --_g:calc(100% - var(--w)/2)/calc(var(--w)*(1 + 1/var(--r)) - 2*(var(--s) + var(--_d)));
  background: repeating-conic-gradient(from 45deg,#0000 0 25%,#0005 0 50%) var(--_g);
  mask:       repeating-conic-gradient(from 45deg,#000  0 25%,#0005 0 50%) var(--_g);
  clip-path: polygon(var(--l) 0,var(--_d) var(--s),calc(100% - var(--_d)) var(--s),calc(100% - var(--l)) 0,100% var(--l),calc(100% - var(--s)) var(--_d),calc(100% - var(--s)) calc(100% - var(--_d)),100% calc(100% - var(--l)),calc(100% - var(--l)) 100%,calc(100% - var(--_d)) calc(100% - var(--s)),var(--_d) calc(100% - var(--s)),var(--l) 100%,0 calc(100% - var(--l)),var(--s) calc(100% - var(--_d)),var(--s) var(--_d),0 var(--l))
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="rNRxJPj" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/rNRxJPj">
  Adhesive tape for your images</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>