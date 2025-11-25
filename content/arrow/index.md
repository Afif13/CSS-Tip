---
layout: layouts/post.njk
title: Direction-Aware Arrow Shape using corner-shape
description: Combining corner-shape and logical properties to create direction-aware shapes.
date: 2025-11-25
tags: posts
---

We can use [the new `corner-shape` to draw different CSS Shapes](/corner-shape/). And since it relies on `border-radius`, we can use the logical properties to create a direction-aware arrow that adjusts based on both the direction and the writing mode.

{% image "./image.png", "CSS-only direction-aware arrow shape" %}

```css
.arrow {
  --h: 80px; /* head */
  --t: 50px; /* tail */
  
  inline-size: calc(var(--h) + var(--t));
  block-size: calc(2*var(--h));
  border-start-start-radius: var(--t);
  border-end-start-radius: var(--t);
  border-start-end-radius: var(--h);
  border-end-end-radius: var(--h);
  corner-start-start-shape: notch;
  corner-end-start-shape: notch;
  corner-start-end-shape: bevel;
  corner-end-end-shape: bevel;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="YPqezLv" data-pen-title="Direction-aware arrow shape" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/YPqezLv">
  Direction-aware arrow shape</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

The code can be less restrictive and more flexible if you want to consider only the direction and keep a horizontal writing mode.

```css
.arrow {
  --h: 80px; /* head */
  --t: 45px; /* tail */
  
  width: 200px;
  height: 140px;
  border-start-start-radius: calc(100% - var(--h)) var(--t);
  border-end-start-radius: calc(100% - var(--h)) var(--t);
  border-start-end-radius: var(--h) 50%;
  border-end-end-radius: var(--h) 50%;
  corner-start-start-shape: notch;
  corner-end-start-shape: notch;
  corner-start-end-shape: bevel;
  corner-end-end-shape: bevel;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="EaKQaNE" data-pen-title="Direction-aware arrow shape (less restrictive)" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/EaKQaNE">
  Direction-aware arrow shape (less restrictive)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>