---
layout: layouts/post.njk
title: Place your image inside a 3D gift box
description: a cool 3D effect to create a image gift box
date: 2023-12-19
tags: posts
---

Place your image inside a 3D box and reveal it with a cool hover effect. Perfect for your virtual gifts 🎁
* No extra element (only the `<img>` tag)
* No pseudo-elements
* Optimized with CSS Variables


{% image "./image.png", "A 3D box with image" %}

```css
@property --h {
  syntax: "<length>";
  initial-value: 0px;
  inherits: true;
}

img {
  --w: 150px; /* image size */
  --b: 12px;  /* the border */
  --d: 30px;  /* the 3D depth */
  --c: #d81a14;
  
  --_w: calc(var(--w) + 2*var(--b));
  width: calc(var(--_w) + var(--d));
  aspect-ratio: 1;
  padding-top: min(var(--h) - var(--b),var(--w));
  border: solid #0000;
  border-width: var(--b) calc(var(--b) + var(--d)) calc(var(--b) + var(--d)) var(--b);
  box-sizing: border-box;
  object-fit: cover;
  object-position: bottom;
  background: 
    linear-gradient(color-mix(in srgb,var(--c),#fff 25%) 0 0) no-repeat
     0 0/calc(100% - var(--d)) calc(100% - var(--d) + var(--h) - var(--_w)),
    conic-gradient(at right var(--d) bottom var(--d),
     #0004 37.5%,#0008 0 75%,#0000 0) var(--c);
  background-origin: border-box;
  clip-path: polygon(0 calc(var(--h) - var(--_w)),calc(100% - var(--d)) calc(var(--h) - var(--_w)),calc(100% - var(--d)) 0,100% var(--d),100% 100%,var(--d) 100%,0 calc(100% - var(--d)));
  box-shadow: 0 0 0 999px color-mix(in srgb,var(--c),#fff 25%);
  --h: calc(var(--_w));
  transition: --h .6s linear;
}
img:hover {
  --h: 0px;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="LYaPPPo" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/LYaPPPo">
  Image gift box (hover to reveal)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>