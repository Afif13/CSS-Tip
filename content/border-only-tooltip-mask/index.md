---
layout: layouts/post.njk
title: A border-only Tooltip using mask
description: Use CSS mask to create a border-only tooltip with a gradient coloration
date: 2023-02-08
tags: posts
---

Create a border-only Tooltip with a few lines of code
* One element
* Less than 20 CSS declarations
* Support gradient coloration
* Support `border-radius`
* Optimized with CSS variables

{% image "./css-tooltip.png", "A border-only tooltip with gradient coloration" %}

```css
.tooltip {
  --r: 30px; /* border radius*/
  --b: 8px;  /* border length */
  --s: 55px; /* arrow size */
  --a: 90deg; /* angle of the arrow */
  --c: linear-gradient(60deg,#E84A5F,#355C7D);
  
  max-width: 410px;
  font-size: 20px;
  padding: calc(var(--r) + var(--b));
  position: relative;
  font-weight: bold;
  font-family: sans-serif;
}
.tooltip::before {
  content: "";
  position: absolute;
  inset: calc(-1*var(--s));
  border-radius: calc(var(--r) + var(--s));
  border: var(--s) solid #0000;
  padding: var(--b);
  background: var(--c) border-box;
  --_m:/100% var(--s) no-repeat conic-gradient(from calc(var(--a)/-2),#000 var(--a),#0000 0),
       linear-gradient(#000 0 0);
  mask: 
    50% calc(100% - var(--b)) var(--_m) content-box, 
    bottom var(--_m) padding-box;
  mask-composite: exclude;
}
```


<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="rNrgdzJ" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/rNrgdzJ">
  Border-only Tooltip with a gradient coloration</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


