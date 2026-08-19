---
layout: layouts/post.njk
title: Hover Proximity with Scroll-Driven Animations
description: A fancy hover effect in a 2D responsive grid powered by modern CSS
date: 2026-08-19
tags: posts
---

Hover proximity? It's when you affect the hovered element and a few surrounding elements. A fancy effect made possible using modern CSS.

{% image "./image.png", "CSS-only hover proximity" %}


⚠️ (Chromium-only for now) ⚠️

<p class="codepen" data-height="800" data-pen-title="Hover Proximity with scroll-driven animations" data-preview="true" data-default-tab="result" data-slug-hash="ZYLgGBM" data-user="t_afif" style="height: 800px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZYLgGBM">
  Hover Proximity with scroll-driven animations</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

We first define a responsive grid structure and calculate [the coordinates of each element](/grid-information/):

```css
.container {
  --s: 50px; /* size */
  --g: 0px;  /* gap */
  
  display: grid;
  grid-template-columns: repeat(auto-fill,minmax(var(--s),1fr));
  gap: var(--g);
  container-type: inline-size;
}
.container > * {
  /* number of columns */
  --n: round(down,(100cqw + var(--g))/(var(--s) + var(--g)));
  /* number of rows */
  --m: round(up,sibling-count()/var(--n));

  /* coordinates */
  --x: round(down,(sibling-index() - 1)/var(--n));
  --y: mod(sibling-index() - 1,var(--n)); 
}
```

Then, we calculate the coordinates of the hovered element using Scroll-Driven animations:

```css
.container {
  overflow: hidden;
  timeline-scope: --_i,--_j;
  animation: --_i linear both,--_j linear both;
  animation-timeline: --_i,--_j;
  animation-range: entry 100% exit 0%;
}
@keyframes --_i { 0% {--_i: 1} to {--_i: 0}}
@keyframes --_j { 0% {--_j: 1} to {--_j: 0}}

.container > * {
  /* coordinates  of the hovered item */
  --i: round(var(--_i)*(var(--m) - 1));
  --j: round(var(--_j)*(var(--n) - 1));
}
.container > *:hover { 
  view-timeline: --_j x,--_i y;
}
```

Finally, we apply some conditional CSS:

```css
.container > *:before {
  /* calculate the distance between each element and the hovered element */
  --_d: hypot(var(--x) - var(--i),var(--y) - var(--j));
  /* use the distance to apply conditional CSS */
  translate: if(
    style(--_d <= 3): 
      calc(sign(var(--y) - var(--j))*max(0px,15px - var(--_d)*2px)) 
      calc(sign(var(--x) - var(--i))*max(0px,15px - var(--_d)*2px));
    else: 0 0;
   );
  scale: max(.7,1.5 - .2*var(--_d));
}
```

A bit lost? Stay tuned for a detailed article explaining the technique. A technique we can use to create many cool demos!

<p class="codepen" data-height="500" data-pen-title="Hover Proximity with scroll-driven animations" data-preview="true" data-default-tab="result" data-slug-hash="YPNmXEq" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/YPNmXEq">
  Hover Proximity with scroll-driven animations</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

<p class="codepen" data-height="500" data-pen-title="highlight same row and column on hover" data-preview="true" data-default-tab="result" data-slug-hash="WbRVvdz" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/WbRVvdz">
  highlight same row and column on hover</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


<p class="codepen" data-height="500" data-pen-title="highlight diagonal on hover" data-preview="true" data-default-tab="result" data-slug-hash="wBgVayP" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/wBgVayP">
  highlight diagonal on hover</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>