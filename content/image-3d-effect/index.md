---
layout: layouts/post.njk
title: Transform a 2D image into a 3D one
description: A few lines of code to transform your image into 3D
date: 2023-05-17
tags: posts
---

Transform your 2D image into a 3D one using a few lines of code
* No extra element (only the `<img>` tag)
* No pseudo-element
* Nice animation on hover 🤩


{% image "./image.png", "3D images using CSS" %}

```css
img {
  --d: 18px;  /* the depth */
  --a: 20deg; /* the angle */
  
  /* the below value is based on the depth and the angle.
     the formula is a bit difficult to express so we update it manually
  */
  --x: 10px;
  
  width: 250px; /* control the size */
  aspect-ratio: 1.1; /* you can use 1 as ratio but I found 1.1 a little better */
  padding-block: var(--d);
  transform: perspective(400px) rotateY(calc(var(--_i,1)*var(--a)));
  outline: var(--d) solid #0008;
  outline-offset: calc(-1*var(--d));
  --_d: calc(100% - var(--d));
  --_l: 0px;
  --_r: 0px;
  clip-path: polygon(
    var(--_l) calc(var(--_d) - var(--x)),
    var(--_l) calc(var(--d)  + var(--x)), 
    var(--d) var(--d),var(--_d) var(--d),
    calc(var(--_d) + var(--_r)) calc(var(--d)  + var(--x)),
    calc(var(--_d) + var(--_r)) calc(var(--_d) - var(--x)),  
    var(--_d) var(--_d),var(--d) var(--_d)
   );
  transition: transform .3s,--_r .15s,--_l .15s .15s;
  transition-timing-function: linear;
}
img:hover {
  --_l: var(--d);
  --_r: var(--d);
  --_i: -1;
  transition-delay: 0s,.15s,0s;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="yLRRBKj" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yLRRBKj">
  3D images with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

