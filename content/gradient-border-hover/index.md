---
layout: layouts/post.njk
title: Rounded gradient border with hover effect
description: Use modern CSS tricks to create a nice hover effect with a gradient border
date: 2023-11-28
tags: posts
---

Add a fancy hover effect to your image with a gradient border
* No extra element (only the `<img>` tag)
* No pseudo-element
* Powered by CSS mask & @property

{% image "./image.png", "rounded gradient border" %}

```css
@property --h {
  syntax: "<percentage>";
  initial-value: 0%;
  inherits: true;
}

img {
  --b: 15px; /* border width */
  --g: 10px; /* gap */
  --c: red;
  
  border-radius: 50%;
  padding: calc(var(--b) + var(--g));
  background: conic-gradient(from 180deg in oklch longer hue, red 0 0);
  mask:
    radial-gradient(farthest-side,
      #000  calc(100% - var(--b) - var(--g) - 1px),
      #0000 calc(100% - var(--b) - var(--g)) 
            calc(100% - var(--b)),
      #000  calc(100% - var(--b) + 1px)),
    conic-gradient(from 180deg,
     #0000   calc(var(--p) - var(--h)),
     #000  0 var(--p),
     #0000,
     #000  0 calc(var(--p) + var(--h)),
     #0000 0),
    linear-gradient(#000 0 0) content-box;
  mask-composite: intersect,add;
  --p: 0%;
  transition: --h .5s linear,scale .5s;
}
img:hover {
  --h: 100%;
  --p: 100%;
  scale: 1.1;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="KKJedrm" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/KKJedrm">
  Fancy gradient border with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>