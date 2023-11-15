---
layout: layouts/post.njk
title: Add a 3D style to your text
description: Add a touch of 3D to your text with some gradients tricks
date: 2023-11-15
tags: posts
---

Add a touch of 3D to your text using a few lines of code
* Minimal HTML
* Works with multi-line text
* Less than 10 CSS declarations


{% image "./image.png", "A 3D text using CSS" %}

```css
h2 { 
  --d: .3em; /* control the depth */
  line-height: 2; /* control the distance between boxes */
}
h2 span { 
  padding-block: .1em calc(.1em + var(--d));
  padding-inline:.2em calc(.2em + var(--d));
  box-decoration-break: clone;
  background:
    conic-gradient(at right var(--d) bottom var(--d),#0004 37.5%,#0008 0 75%,#0000 0) 
    #d81a14; /* the main color */
  mask: linear-gradient(45deg,#0000 calc(var(--d)*cos(45deg)),#000 0 calc(100% - var(--d)*cos(45deg)),#0000 0);
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="ZEwJLdL" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZEwJLdL">
  CSS only 3D multi-line text</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
