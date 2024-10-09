---
layout: layouts/post.njk
title: Puzzle shapes using CSS mask
description: A few lines of code to craft different puzzle shapes
date: 2024-10-09
tags: posts
---

Create different kind of [puzzle shapes](https://css-shape.com/puzzle/) using a few lines of code
* Single element (Works with `<img>`)
* Optimized with CSS variables
* Powered by CSS mask


{% image "./image.png", "CSS-only puzzle shapes" %}

```css
.puzzle {
  --r: 30px;  /* control the circle radius */
  --s: 200px; /* control the main size */

  width: var(--s);
  height: calc(var(--s) + var(--r));
  mask: 
    radial-gradient(var(--r) at 50% calc(100% - var(--r)),#000 calc(100% - 1px),#0000), 
    radial-gradient(var(--r) at right,#0000 calc(100% - 1px),#000) 
     0 0/100% calc(100% - var(--r)) no-repeat;
}
```

Find more variations here: [css-shape.com/puzzle](https://css-shape.com/puzzle/)

A demo using the different shapes to create a grid of images

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="RwXoWvr" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/RwXoWvr">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

