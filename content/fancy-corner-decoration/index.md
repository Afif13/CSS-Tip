---
layout: layouts/post.njk
title: Fancy corner decoration for your images
description: A few lines of code for a cool corner decoration
date: 2024-01-05
tags: posts
---

Add a fancy decoration to the corners of your image using a few lines of code
* No extra element (only the `<img>` tag)
* No pseudo-element
* Optimized with CSS Variables


{% image "./image.png", "corner-only decoration for images" %}

```css
img {
  --w: 250px; /* image width */
  --r: 1;     /* image ratio */
  --c: 113px; /* control the size of the decoration */
  
  width: var(--w);
  padding: 10px; /* control the outer space  */
  box-sizing: border-box;
  aspect-ratio: var(--r);
  object-fit: cover;
  --_g:calc(100% - var(--w)/2)/calc(var(--w)*(1 + 1/var(--r)) - var(--c));
  background: repeating-conic-gradient(from 45deg,#0000 0 25%,#0005 0 50%) var(--_g);
  mask:       repeating-conic-gradient(from 45deg,#000  0 25%,#0005 0 50%) var(--_g);
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="LYaGzre" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/LYaGzre">
  Fancy corner decoration for images</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>