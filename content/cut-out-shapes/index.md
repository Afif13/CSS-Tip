---
layout: layouts/post.njk
title: Cut-out shapes using clip-path
description: Invert any kind of polygon shapes following a simple steps
date: 2024-06-19
tags: posts
---

A simple code to invert any kind of shape created using `clip-path: polygon()`. An easy way to create Cut-out shapes.

{% image "./image.png", "CSS-only Cut-out shapes using clip-path" %}

```css
.shape {
  --shape: X0 Y0, X1 Y1, X2 Y2, ... , Xn Yn, X0 Y0; /* the first value is repeated */
  
  /* the main shape */
  clip-path: polygon(var(--shape)); 
}
.shape.invert {
  --s: -20px; /* Control the space */
  padding: calc(-1*var(--s));
  /* the inverted shape */
  clip-path: polygon(evenodd,var(--s) var(--s),calc(100% - var(--s)) var(--s),calc(100% - var(--s)) calc(100% - var(--s)),var(--s) calc(100% - var(--s)),var(--s) var(--s),var(--shape)) content-box; 
}
```

The first part before `var(--shape)` is static. It's the same for all the shapes, you don't need to change it. Don't forget the "content-box" at the end!

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="gOJvdav" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/gOJvdav">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [verpex.com/blog/website-tips/how-to-create-cut-out-shapes-using-the-clip-path-property](https://verpex.com/blog/website-tips/how-to-create-cut-out-shapes-using-the-clip-path-property) 