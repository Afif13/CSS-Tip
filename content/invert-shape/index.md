---
layout: layouts/post.njk
title: Invert CSS Shapes using shape()
description: A simple trick to get the cut-out version of any shape created using shape() 
date: 2025-07-01
tags: posts
---

Do you want to invert a shape created using `clip-path: shape()`? With a simple code, you can have both the main shape and its cut-out version.

{% image "./image.png", "CSS-only Cut-out shapes using shape()" %}

```css
.shape {
  /* You add "evenodd" at the start and "var(--i,)" at the end */
  clip-path: shape(evenodd from .... var(--i,));
}
.invert { /* by adding the "invert" class, the shape is inverted! */
  --i:,move to 0 0, hline to 100%, vline to 100%, hline to 0;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="ogXOmWa" data-pen-title="Inverting shapes using shape()" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ogXOmWa">
  Inverting shapes using shape()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

We can add an extra variable and control the space around the shape when inverted:

```css
.shape {
  clip-path: shape(evenodd from ... var(--i,)) content-box; /* content-box at the end */
}
.invert {
  --d: 20px; /* this will control the space around the inverted shape */
  padding: var(--d);
  --i: ,move to calc(-1*var(--d)) calc(-1*var(--d)),
        hline to calc(100% + var(--d)),
        vline to calc(100% + var(--d)),
        hline to calc(-1*var(--d));
  box-sizing: content-box;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="ZYGZwXJ" data-pen-title="Inverting shapes using shape()" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZYGZwXJ">
  Inverting shapes using shape()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

If you want to do the same with `clip-path: polygon()`, check this: [Cut-out shapes using clip-path](/cut-out-shapes/)