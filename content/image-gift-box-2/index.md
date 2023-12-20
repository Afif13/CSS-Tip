---
layout: layouts/post.njk
title: Place your image inside a 3D gift box II
description: a cool 3D effect to create a image gift box
date: 2023-12-20
tags: posts
---

Here is another variation of [the previous effect](/image-gift-box/). Now you can open the gift box from both sides 🎁

Still using only the `<img>` tag (No extra elements, No pseudo-elements) and a touch of magic 🪄


{% image "./image.png", "A 3D box with image" %}

```css
@property --h {
  syntax: "<length>";
  initial-value: 0px;
  inherits: true;
}

img {
  --w: 200px; /* image size */
  --b: 12px;  /* the border */
  --d: 20px;  /* the depth */
  --c: #d81a14;
  
  width: var(--w);
  aspect-ratio: 1;
  --h: calc(var(--w)/2);
  padding: var(--b) max(var(--h),var(--b));
  box-sizing: border-box;
  object-fit: cover;
  object-position: center;
  background: 
    linear-gradient(#0004 0 0) no-repeat
     50%/0% 100% var(--c) border-box;
  clip-path: polygon(calc(var(--h) - var(--w)/2) 0,calc(100% + var(--w)/2 - var(--h)) 0,calc(100% + var(--w)/2 - var(--h)) 100%,100% 100%,calc(100% - var(--d)) calc(100% + var(--d)),var(--d) calc(100% + var(--d)),0 100%,calc(var(--h) - var(--w)/2) 100%);
  box-shadow: 
    0 var(--d) #0008,
    0 0 0 999px var(--c);
  transition: .6s linear;
  transition-property: --h,background-size;
}
img:hover {
  background-size: 100% 100%;
  --h: 0px;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="yLwBVGQ" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yLwBVGQ">
  Image gift box II (hover to reveal)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>