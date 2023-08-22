---
layout: layouts/post.njk
title: Fancy frame for your image with hover effect
description: A nice looking frame around your image with a cool hover effect
date: 2023-08-22
tags: posts
---

Add a nice frame around your image with a cool hover effect
* No extra element (only the `<img>` tag)
* No pseudo-elements
* Only 4 gradients
* Optimized with CSS variables


{% image "./image.png", "CSS only frame with hover effect around an image" %}

```css
@property --s {
  syntax: "<length>";
  initial-value: 0px;
  inherits: true;
}

img {
  --t: 3px;  /* control the thickness (corner = 3*edge) */
  --s: 40px; /* control the size of the corners (that also affect the size of the edges) */
  --g: 8px;  /* control the gap */
  --c: #755C3B;
  
  padding: calc(2*var(--t) + var(--g));
  border: var(--t) solid #0000;
  background:
    conic-gradient(at var(--s) calc(3*var(--t)),#0000 75%,var(--c) 0)
     0 0/calc(100% - var(--s)) calc(100% - 3*var(--t)) border-box,
    conic-gradient(at calc(3*var(--t)) var(--s),#0000 75%,var(--c) 0)
     0 0/calc(100% - 3*var(--t)) calc(100% - var(--s)) border-box,
    linear-gradient(  0deg,var(--c) calc(2*var(--t)),#0000 0) 
      50% var(--t)/calc(100% - 2*(var(--s) + var(--g))) 100% 
      repeat-y padding-box,
    linear-gradient(-90deg,var(--c) calc(2*var(--t)),#0000 0) 
      var(--t) 50%/100% calc(100% - 2*(var(--s) + var(--g))) 
      repeat-x padding-box;
  transition: --s .5s;
}
img:hover {
   --s: 80px;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="XWoJRLr" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWoJRLr">
  Fancy image frame with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>