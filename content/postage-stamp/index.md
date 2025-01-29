---
layout: layouts/post.njk
title: Turn an image into a postage stamp
description: A few lines of code to create a cool postage stamp shape
date: 2024-03-14
tags: posts
---

Transform your image into a cool postage stamp with a few lines of code
* No extra element (only the `<img>` tag)
* Only two CSS gradients
* Works with any image size
* Easy to adjust using CSS variables


{% image "./image.png", "CSS-only overlay reveal animation" %}

```css
img {
  --r: 20px; /* control the radius of the circles */
  padding: var(--r);
  filter: grayscale(.4) drop-shadow(0 0 1px #0005) drop-shadow(0 0 1px #0005);
  background: 
    radial-gradient(50% 50%,#0000 65%,#fff 67%) round 
     var(--r) var(--r)/calc(2*var(--r)) calc(2*var(--r));
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="gOXxvgM" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/gOXxvgM">
  CSS-only Stamp effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>