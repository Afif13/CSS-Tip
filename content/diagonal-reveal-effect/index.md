---
layout: layouts/post.njk
title: "Diagonal split & reveal animation"
description: Use clip-path to create a nice hover effect to reveal images
date: 2022-08-19
tags: posts
---

Reveal your images with a cool hover effect using a few lines of code
* Minimal HTML (2 `<img>` inside a container)
* Less than 15 CSS declaration
* Optimized with CSS variables


{% image "./hover-effect.png", "A fancy hover effect using CSS clip-path" %}

```css
.gallery {
  --g: 8px; /* the gap */
  
  display: grid;
}
.gallery > img {
  --_p: calc(-1*var(--g));
  grid-area: 1/1;
  transition: .4s .1s;
}
.gallery > img:first-child {
  clip-path: polygon(0 0, calc(100% + var(--_p)) 0 , 0 calc(100% + var(--_p)))
}
.gallery > img:last-child {
  clip-path: polygon(100% 100%, 100% calc(0% - var(--_p)), calc(0% - var(--_p)) 100%)
}
.gallery:hover > img:last-child,
.gallery:hover > img:first-child:hover{
  --_p: calc(50% - var(--g));
}
.gallery:hover > img:first-child,
.gallery:hover > img:first-child:hover + img{
  --_p: calc(-50% - var(--g));
}
```

<p class="codepen" data-height="350" data-default-tab="result" data-slug-hash="LYdqGKQ" data-preview="true" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/LYdqGKQ">
  Dual image with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [css-tricks.com/css-grid-and-custom-shapes-part-3](https://css-tricks.com/css-grid-and-custom-shapes-part-3/#aa-the-split-image-reveal)