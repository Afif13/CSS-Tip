---
layout: layouts/post.njk
title: A fancy frame with Zig-Zag borders
description: Use modern CSS to create a Zig-Zag box
date: 2024-04-18
tags: posts
---

Use modern CSS to create a fancy [Zig-Zag border around images](https://css-shape.com/zig-zag-box/) using a few lines of code.
* Only one element (the `<img>` tag)
* No pseudo-element
* Optimized with CSS variables

⚠️ Not suitable for touch screen (the sharp edges may hurt you) use [wavy borders](/image-wavy-borders/)


{% image "./image.png", "CSS-only zig-zag borders" %}

```css
img {
  --s: 16px;  /* control the size of the spikes */
  --w: 250px; /* preferred image width */
  
  width: round(var(--w),4*var(--s)); 
  aspect-ratio: 1;
  --_m:#0000 0 calc(2*atan(.5)),#000 0 50%;
  mask:
    repeating-conic-gradient(from atan(2) at 50% var(--s),var(--_m))
     calc(2*var(--s)) calc(-1*var(--s))/calc(4*var(--s)) 100% intersect,
    repeating-conic-gradient(from atan(-.5) at var(--s),var(--_m))
     calc(-1*var(--s)) calc(2*var(--s))/100% calc(4*var(--s));
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="OJGBvmp" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/OJGBvmp">
  CSS-only Zig-Zag box</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>