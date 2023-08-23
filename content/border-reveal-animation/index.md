---
layout: layouts/post.njk
title: Border reveal animation on hover
description: A nice animation to reveal your border on hover 
date: 2023-08-23
tags: posts
---

Add a simple border around your image with a nice hover effect
* No extra element (only the `<img>` tag)
* No pseudo-elements
* Only 3 Gradients
* Less than 15 CSS declarations


{% image "./image.png", "animation to reveal a border around the image" %}

```css
@property --p {
  syntax: "<percentage>";
  initial-value: 0%; /* you can start at 50% for a different effect */
  inherits: true;
}

img {
  --t: 5px;  /* control the thickness */
  --s: 40px; /* control the size of the dash  */
  --g: 8px;  /* control the gap */
  --c: #68B3AF;
  
  padding: 
    calc(var(--g) + var(--t)) var(--g)
    var(--g) calc(var(--g) + var(--t));
  border: solid #0000;
  border-width: 0 var(--t) var(--t) 0; 
  background:
    conic-gradient(at var(--p) var(--p), #0000 75%,var(--c) 0)
     0 0/var(--s) var(--s) round padding-box border-box;
  mask: 
    conic-gradient(
      from 90deg at calc(2*var(--t)) calc(2*var(--t)),
      #0000 25%,#000 0) calc(-1*var(--t)) calc(-1*var(--t)),
    linear-gradient(#000 0 0) content-box;
  transition: --p .6s;
}
img:hover {
   --p: 100%;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="xxmGLwr" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/xxmGLwr">
  Border Reveal on hover</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>