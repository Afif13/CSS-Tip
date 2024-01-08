---
layout: layouts/post.njk
title: Fancy Rounded frame around your images
description: Combine gradients and CSS mask to create a fancy frame around an image
date: 2022-11-01
tags: posts
---

Add a nice frame around your image using a few lines of code
* One element (The `<img>` tag)
* No pseudo-element
* Only 3 CSS properties
* Optimized with CSS variables

{% image "./fancy-frame.png", "An image with a fancy rounded frame" %}

```css
img {
  --s: 20px;    /* size of the frame */
  --g: 10px;    /* the gap */
  --c: #FA6900; 
  
  padding: calc(var(--g) + var(--s));
  background: 
    radial-gradient(farthest-side,var(--c) 97%,#0000)
    0 0/calc(2*var(--s)) calc(2*var(--s)) round;
  --_m:
    conic-gradient(from 90deg at calc(2*var(--s)) calc(2*var(--s)),#0000 25%,#000 0)
     calc(-1*var(--s)) calc(-1*var(--s)),
    linear-gradient(#000 0 0) content-box;
  -webkit-mask: var(--_m);
          mask: var(--_m);
}
```


<p class="codepen" data-height="350" data-default-tab="result" data-slug-hash="GROJrNw" data-preview="true" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/GROJrNw">
  Cool frame image</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More detail: [css-tricks.com/fancy-image-decorations-masks-and-advanced-hover-effects](https://css-tricks.com/fancy-image-decorations-masks-and-advanced-hover-effects/)