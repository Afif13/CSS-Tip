---
layout: layouts/post.njk
title: Triangle shape with rounded corners
description: A few lines of code to create a triangle with rounded corner using only CSS
date: 2024-01-19
tags: posts
---

A modern way to create a triangle with rounded corners
* Only one element (no pseudo-elements)
* Only three CSS properties
* One variable to control the radius


{% image "./image.png", "triangles with rounded corners" %}

```css
.tri {
  --r: 40px; /* the radius */
  
  width: 300px;
  aspect-ratio: 1/cos(30deg);
  mask:
    conic-gradient(from -30deg at 50% calc(200% - 3*var(--r)/2),#000 60deg,#0000 0)
     0 100%/100% calc(100% - 3*var(--r)/2) no-repeat,
    radial-gradient(var(--r) at 50% calc(2*var(--r)),#000 98%,#0000 101%),
    radial-gradient(var(--r),#000 98%,#0000 101%) space no-repeat
     0 100%/calc(2*tan(60deg)*var(--r)) calc(2*var(--r));
  clip-path: polygon(50% 0,100% 100%,0 100%);
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="QWovwoW" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/QWovwoW">
  Rounded triangles (the modern way)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

We can also have a cool hover effect

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="poYPLbp" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/poYPLbp">
  Rounded triangles with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>