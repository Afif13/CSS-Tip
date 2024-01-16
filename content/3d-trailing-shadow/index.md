---
layout: layouts/post.njk
title: 3D trailing shadows for images
description: A simple trick to add a 3D shadow to your images
date: 2023-07-04
tags: posts
---

Add a 3D trailing shadow to your image with a few lines of code
* No extra element (only the `<img>` tag)
* No pseudo-element
* Less than 10 CSS declarations
* No scrollbar issue


{% image "./image.png", "A 3D trailing shadow for images" %}

```css
img {
  --c: #CBE86B; /* the main color */
  --t: 5px; /* thickness of the outline */
  
  width: 200px; /* the image size */
  aspect-ratio: 1; /* only square images, don't change this */
  border-image: 
    linear-gradient(45deg,
      color-mix(in srgb,var(--c),#000 20%) 50%,
      color-mix(in srgb,var(--c),#000 40%) 0) 
     fill 0//9999px;
  clip-path: 
    polygon(0 100%,0 0,100% 0,
      calc(100% + 9999px) 9999px,
      9999px calc(100% + 9999px));
  outline: var(--t) solid var(--c);
  outline-offset: calc(-1*var(--t));
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="mdQwgMO" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/mdQwgMO">
  3D trailing shadow for images</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

Related: [smashingmagazine.com/2024/01/css-border-image-property/](https://www.smashingmagazine.com/2024/01/css-border-image-property/)