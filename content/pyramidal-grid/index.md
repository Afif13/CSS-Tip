---
layout: layouts/post.njk
title: Responsive Pramidal Grid of Hexagon Shapes (and more!)
description: A responsive pyramid grid of various shapes without media queries
date: 2026-01-27
tags: posts
---

Following [the previous post](/hexagon-grid/), here is another type of responsive grid: a pyramidal grid of hexagon shapes! Another fancy layout powered by modern CSS, math functions, and without media queries.

{% image "./image.png", "CSS-only responsive pyramidal grid" %}

```css
.container {
  --s: 40px;  /* size  */
  --g: 5px;   /* gap */
  
  display: grid;
  grid-template-columns: repeat(auto-fit, var(--s) var(--s));
  justify-content: center;
  gap: var(--g);
  container-type: inline-size;
}
.container > * {
  grid-column-end: span 2;
  aspect-ratio: cos(30deg);
  border-radius: 50% / 25%;
  corner-shape: bevel;
  margin-bottom: calc((2*var(--s) + var(--g))/(-4*cos(30deg)));
  --_n: round(down,(100cqw + var(--g))/(2*(var(--s) + var(--g))));
  --_i: calc((sibling-index() - 2 + (var(--_n)*(3 - var(--_n)))/2)/(2*var(--_n) - 1));
  --_c: mod(var(--_i),1);
  --_j: calc(sqrt(2*sibling-index() - 1.75) - .5);
  --_d: mod(var(--_j),1);
  grid-column-start: 
    if(
      style((--_i >= 1) and (--_c: 0)): 2; 
      style(--_d: 0): max(0,var(--_n) - var(--_j));
    );
}
```

Chrome-only for now. 

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="bNeYmwb" data-pen-title="Responsive pyramid of hexagon shapes" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/bNeYmwb">
  Responsive pyramid of hexagon shapes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

We can get more variation by adjusting the code slightly.

Rhombus grid:

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="NPrwOXG" data-pen-title="Responsive Pyramid of Rhombus Shapes" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/NPrwOXG">
  Responsive Pyramid of Rhombus Shapes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Octagon grid:

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="emzePGW" data-pen-title="Responsive Pyramid of Octagon Shapes" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/emzePGW">
  Responsive Pyramid of Octagon Shapes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


Another hexagon grid:

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="XJKzxRg" data-pen-title="Responsive Pyramid of Hexagon Shapes" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/XJKzxRg">
  Responsive Pyramid of Hexagon Shapes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
 </p>

And why circles as well: 

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="YPWEJQR" data-pen-title="Responsive Pyramid of Circles" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/YPWEJQR">
  Responsive Pyramid of Circles</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>