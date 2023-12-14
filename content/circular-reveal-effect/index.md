---
layout: layouts/post.njk
title: A circular reveal effect for your images
description: A few lines of code to create a fancy reveal effect on images
date: 2023-12-14
tags: posts
---

Add a fancy reveal effect to your images with a few lines of code
* No extra element (only the `<img>` tag)
* No pseudo-elements
* Powered by CSS Variables & @property


{% image "./image.png", "CSS-only reveal effect on hover" %}

```css
@property --a {
  syntax: "<angle>";
  initial-value: 0deg;
  inherits: true;
}

img {
  --w: 200px; /* image width*/
  --b: 10px; /* border thickness */
  --g: 5px; /* the gap */
  --c: #5E8C6A;
  
  width: var(--w);
  padding: calc(1.5*var(--w));
  margin: calc(var(--b) + var(--g) - 1.5*var(--w));
  border-radius: 50%;
  --_p:calc(var(--w)/2 + var(--g) + var(--b)) 
    at calc(50% + 25%*cos(var(--a))) calc(75% - 25%*sin(var(--a)));
  background: radial-gradient(var(--_p),
      #0000    calc(100% - var(--b) - 1px),
      var(--c) calc(100%  - var(--b)));
  transform-origin: 50% 75%;
  rotate: calc(var(--a) - 90deg);
  clip-path: circle(var(--_p));
  transition: --a .5s;
}
img:hover {
  --a: 90deg;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="wvNbXrE" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/wvNbXrE">
  Circular reveal hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>