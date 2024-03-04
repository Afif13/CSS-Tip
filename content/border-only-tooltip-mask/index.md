---
layout: layouts/post.njk
title: A border-only Tooltip using mask
description: Use CSS mask to create a border-only tooltip with a gradient coloration
date: 2023-02-08
tags: posts
---

Create a border-only Tooltip with a few lines of code
* One element
* Support gradient coloration
* Support `border-radius`
* Optimized with CSS variables

{% image "./image.png", "CSS border-only tooltip with gradient coloration" %}

```css
.tooltip {
  /* triangle dimension */
  --a: 90deg; /* angle */
  --h: 1.5em; /* height */
  
  position: relative;
  z-index: 0;
}
.tooltip:before,
.tooltip:after {
  content: "";
  position: absolute;
  z-index: -1;
  inset: 0;
  background: linear-gradient(60deg,#E84A5F,#355C7D);  /* your coloration */
}
.tooltip:before {
  padding: 8px; /* the border width */
  border-radius: 1.2em; /* the radius */
  background-size: 100% calc(100% + var(--h));
  clip-path: polygon(0 100%,0 0,100% 0,100% 100%,
    calc(50% + var(--h)*tan(var(--a)/2) - var(--b)*tan(45deg - var(--a)/4)) 100%,
    calc(50% + var(--h)*tan(var(--a)/2) - var(--b)*tan(45deg - var(--a)/4)) calc(100% - var(--b)),
    calc(50% - var(--h)*tan(var(--a)/2) + var(--b)*tan(45deg - var(--a)/4)) calc(100% - var(--b)),
    calc(50% - var(--h)*tan(var(--a)/2) + var(--b)*tan(45deg - var(--a)/4)) 100%);
  mask: linear-gradient(#000 0 0) content-box,linear-gradient(#000 0 0);
  mask-composite: exclude;
}
.tooltip:after {
  bottom: calc(-1*var(--h));
  clip-path: polygon(
    calc(50% + var(--h)*tan(var(--a)/2)) calc(100% - var(--h)),50% 100%,
    calc(50% - var(--h)*tan(var(--a)/2)) calc(100% - var(--h)),
    calc(50% - var(--h)*tan(var(--a)/2) + var(--b)*tan(45deg - var(--a)/4)) calc(100% - var(--h) - var(--b)),
    50% calc(100% - var(--b)/sin(var(--a)/2)),
    calc(50% + var(--h)*tan(var(--a)/2) - var(--b)*tan(45deg - var(--a)/4)) calc(100% - var(--h) - var(--b)));
}
```


<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="rNrgdzJ" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/rNrgdzJ">
  Border-only Tooltip with a gradient coloration</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More Tooltip shapes: [css-generators.com/tooltip-speech-bubble](https://css-generators.com/tooltip-speech-bubble/)

