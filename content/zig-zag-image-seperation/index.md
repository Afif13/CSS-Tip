---
layout: layouts/post.njk
title: Zig Zag sepration between images with hover effect
description: A fancy image sepration with zig-zag shapes and cool hover effect
date: 2023-08-21
tags: posts
---


Place 2 images next to each other with a Zig-Zag separation ⚡️
* Minimal HTML code
* Less than 25 CSS declarations
* Optimized with CSS variables
* Nice hover effect

Zig-Zag edge generator 👉 [css-generators.com/custom-borders](http://css-generators.com/custom-borders)

{% image "./image.png", "Zig Zag seperation between two images" %}

```css
.gallery {
  --z: 32px;  /* control the zig-zag  */
  --s: 360px; /* control the size */
  --g: 8px;   /* control the gap */
  
  display: grid;
  gap: var(--g);
  width: calc(2*var(--s) + var(--g));
  grid-auto-flow: column;
}
.gallery > img {
  width: 0;
  min-width: calc(100% + var(--z)/2);
  height: var(--s);
  mask: var(--mask);
}
.gallery > img:hover {
  width: calc(var(--s)/2);
}
.gallery > img:first-child {
  place-self: start;
  clip-path: polygon(calc(2*var(--z)) 0,100% 0,100% 100%,0 100%);
  --mask: 
    conic-gradient(from -135deg at right,#0000,#000 1deg 89deg,#0000 90deg) 
      50%/100% calc(2*var(--z)) repeat-y;
}
.gallery > img:last-child {
  place-self: end;
  clip-path: polygon(0 0,100% 0,calc(100% - 2*var(--z)) 100%,0 100%);
  --mask: 
    conic-gradient(from   45deg at left ,#0000,#000 1deg 89deg,#0000 90deg) 
      50% calc(50% - var(--z))/100% calc(2*var(--z)) repeat-y;
}
```


<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="BarmdPB" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/BarmdPB">
  Zig-zag border & cool hover effect </a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More detail: [css-tricks.com/css-grid-and-custom-shapes-part-2](https://css-tricks.com/css-grid-and-custom-shapes-part-2/)