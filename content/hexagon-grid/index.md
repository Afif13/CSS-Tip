---
layout: layouts/post.njk
title: Responsive Hexagon Grid without Media Queries
description: A few lines of modern CSS to create a responsive grid of hexagon shapes (and more!)
date: 2026-01-05
tags: posts
---

Using modern CSS to improve [an old implementation of a responsive hexagon grid](/responsive-hexagon-grid/). `coner-shape` to create [the hexagon shape](/hexagon/) and `sibling-index()` combined with math functions to conditionally apply a margin to only the first element of every other row.

{% image "./image.png", "CSS-only responsive hexagon grid" %}

```css
.container {
  --s: 120px;  /* size  */
  --g: 10px;   /* gap */
  
  display: flex;
  gap: var(--g);
  flex-wrap: wrap;
  container-type: inline-size; /* to be able to query the container width (100cqw) */
}
.container > * {
  width: var(--s);
  /* Create the hexagon shape */
  aspect-ratio: cos(30deg);
  border-radius: 50% / 25%;
  corner-shape: bevel;
  /**/
  margin-bottom: calc(var(--s)/(-4*cos(30deg))); /* Create an overlap between the rows */
  /* Some calculation to add a margin-left to the first element of every other row */
  --_n: round(down,(100cqw + var(--g))/(var(--s) + var(--g)));
  --_m: round(down,(100cqw - (var(--s) - var(--g))/2)/(var(--s) + var(--g)));
  --_c: round(down,1 - mod((sibling-index() - 1 + var(--_m))/(var(--_n) + var(--_m)),1));
  margin-left: calc(var(--_c)*(var(--s) + var(--g))/2);
}
```

Chrome-only for now. Consider [my previous implementation](/responsive-hexagon-grid/) for better support.

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="MYeyyVr" data-pen-title="Responsive Grid of hexagon without media queries" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/MYeyyVr">
  Responsive Grid of hexagon without media queries</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

We can extend the code to consider [more shapes, such as a rhombus and an octagon](/corner-shape/)

```css
.container {
  --s: 100px;  /* size  */
  --g: 10px;   /* gap */
  
  display: flex;
  gap: var(--g);
  flex-wrap: wrap;
  container-type: inline-size;
}
.container > * {
  width: var(--s);
  corner-shape: bevel;
  --_n: round(down,(100cqw + var(--g))/(var(--s) + var(--g)));
  --_m: round(down,(100cqw - (var(--s) - var(--g))/2)/(var(--s) + var(--g)));
  --_c: round(down,1 - mod((sibling-index() - 1 + var(--_m))/(var(--_n) + var(--_m)),1));
  margin-left: calc(var(--_c)*(var(--s) + var(--g))/2);
}
.hexagon > * {
  aspect-ratio: cos(30deg);
  border-radius: 50% / 25%;
  margin-bottom: calc(var(--s)/(-4*cos(30deg)));
}
.rhombus > *  {
  aspect-ratio: 1;
  border-radius: 50%;
  margin-bottom: calc(var(--s)/-2);
}
.octagon {
  --g: calc(10px + var(--s)/(sqrt(2) + 1));
  gap: 10px var(--g);
}
.octagon > * {
  aspect-ratio: 1;
  border-radius: calc(100%/(2 + sqrt(2)));
  margin-bottom: calc(var(--s)/(-1*(2 + sqrt(2))));
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="WbxwwKj" data-pen-title="Responsive Grid of various shapes" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/WbxwwKj">
  Responsive Grid of various shapes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>