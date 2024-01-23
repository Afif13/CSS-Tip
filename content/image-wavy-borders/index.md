---
layout: layouts/post.njk
title: A fancy frame with wavy borders
description: Place your image inside a frame with wavy borders
date: 2024-01-23
tags: posts
---

Place your image inside a fancy frame! Wavy borders on all the sides 🤩
* Only one element (the `<img>` tag)
* No pseudo-elements
* Optimized with CSS Variables
* First use case of the `round()` function 🥳

{% image "./image.png", "CSS-only images with wavy borders on all the sides" %}

```css
img {
  --s: 40px;  /* control the size of the wave */
  --w: 250px; /* preferred image width */
  --c:#CD8C52;
  
  width: round(var(--w),2*var(--s)); 
  aspect-ratio: 1;
  object-fit: cover;
  padding: var(--s);
  border-radius: calc(1.5*var(--s));
  --R:calc(var(--s)/sqrt(2)) at;
  --g:radial-gradient(var(--R) 50%,var(--c) calc(100% - 1px),#0000) 
     0 0/calc(2*var(--s)) calc(2*var(--s));
  --_c:#0000 100%,var(--c) calc(100% + 1px);
  --_b:calc(2*var(--s)) calc(51% - var(--s)/2) repeat-x;
  background: var(--g),
    radial-gradient(var(--R) 50% calc(100% + var(--s)/2),var(--_c)) 
     var(--s) calc(100% - var(--s)/2)/var(--_b),
    radial-gradient(var(--R) 50% calc(      var(--s)/-2),var(--_c)) 
     var(--s) calc(       var(--s)/2)/var(--_b);
  --_m:var(--s)/calc(51% - var(--s)/2) calc(2*var(--s)) repeat-y;
  mask: var(--g),
    radial-gradient(var(--R) calc(100% + var(--s)/2) 50%,var(--_c))
     calc(100% - var(--s)/2) var(--_m),
    radial-gradient(var(--R) calc(      var(--s)/-2) 50%,var(--_c)) 
     calc(       var(--s)/2) var(--_m);
}
```


<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="qBvXXBe" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/qBvXXBe">
  CSS-only wavy edges</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

