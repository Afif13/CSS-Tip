---
layout: layouts/post.njk
title: A Rhombus shape with rounded corners for your images
description: 3 lines of code to create a rhombus shape for your image
date: 2023-05-29
tags: posts
---

Transform your image into a Rhombus shape with rounded corners using a few lines of code
* No extra element (only the `<img>` tag)
* No overflow issue
* Only 3 properties
* Optimized with CSS variables


{% image "./image.png", "A Rhombus shape with rounded corners" %}

```css
img {
  --r: 50px; /* the radius */
  aspect-ratio: 1;
  clip-path: 
   polygon(
    50% calc(-.414*var(--r)), calc(100% + .414*var(--r)) 50%, 
    50% calc(100% + .414*var(--r)), calc(-.414*var(--r)) 50%
   );
  --_l: #0000 calc(25% + .707*var(--r)),
       #000 0 calc(75% - .707*var(--r)), #0000 0;
  --_g:/calc(2*var(--r)) calc(2*var(--r)) radial-gradient(#000 70%,#0000 72%);
  mask:
    linear-gradient(45deg,var(--_l)),linear-gradient(-45deg,var(--_l)),
    top var(--_g) no-repeat space,left var(--_g) space no-repeat;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="GRYLqNL" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/GRYLqNL">
  Rhombus image with rounded corner</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


