---
layout: layouts/post.njk
title: A fancy frame with wavy borders II
description: Place your image inside a frame with wavy borders
date: 2024-01-24
tags: posts
---

Improving [the previous effect](/image-wavy-borders/) to consider a gradient coloration instead of a solid color. Using the same code structure.

{% image "./image.png", "CSS-only images with wavy borders on all the sides" %}

```css
img {
  --s: 40px;  /* control the size of the wave */
  --w: 250px; /* preferred image width */
  
  width: round(var(--w),2*var(--s));
  aspect-ratio: 1;
  padding: var(--s);
  border-radius: calc(1.5*var(--s));
  background: conic-gradient(#774F38,#F1D4AF,#45ADA8,#774F38); /* the gradient */
  --R:calc(var(--s)/sqrt(2)) at;
  --m1:calc(2*var(--s)) calc(var(--s)/2) repeat-x exclude;
  --m2:var(--s)/calc(51% - var(--s)/2) calc(2*var(--s)) repeat-y;
  mask:
    radial-gradient(var(--R) 50% calc(100% + var(--s)/2),#0000 calc(100% - 1px),#000) 
     0 0   /var(--m1),
    radial-gradient(var(--R) 50% calc(      var(--s)/-2),#0000 calc(100% - 1px),#000) 
     0 100%/var(--m1),
    radial-gradient(var(--R) 50% calc(100% + var(--s)/2),#000 100%,#0000 calc(100% + 1px)) 
     var(--s) calc(100% - var(--s)/2)/var(--m1),
    radial-gradient(var(--R) 50% calc(      var(--s)/-2),#000 100%,#0000 calc(100% + 1px)) 
     var(--s) calc(       var(--s)/2)/var(--m1),
    radial-gradient(var(--R) calc(100% + var(--s)/2) 50%,#0000 100%,#000 calc(100% + 1px))
     calc(100% - var(--s)/2) var(--m2),
    radial-gradient(var(--R) calc(      var(--s)/-2) 50%,#0000 100%,#000 calc(100% + 1px))
     calc(       var(--s)/2) var(--m2),
    radial-gradient(var(--R) 50%,#000 calc(100% - 1px),#0000) 
     0 0/calc(2*var(--s)) calc(2*var(--s));
  clip-path: inset(calc(.3*var(--s)) round calc(var(--s)/sqrt(2)));
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="GReMgdW" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/GReMgdW">
  CSS-only wavy borders (with gradient coloration)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>