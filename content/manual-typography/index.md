---
layout: layouts/post.njk
title: Manual typography using Scroll-driven animations
description: Use a range slider to manually adjust the font-size of your website (100% CSS)
date: 2024-07-18
tags: posts
---

Add a slider to adjust the `font-size` of your website using modern CSS features.
* 0 JavaScript required (100% CSS)
* Powered by Scroll-driven animations & @property
* Easy to control using CSS variables


```css
@property --i {
  syntax: "<number>";
  inherits: true;
  initial-value: 1; 
}
html {
  --min: 14px;
  --max: 64px;
  --step: 2px;
  
  timeline-scope: --thumb-view;
  animation: i 1s linear;
  animation-timeline: --thumb-view;
  animation-range: entry 100% exit 0%;
  font-size: round(var(--min) + (var(--max) - var(--min))*var(--i),var(--step));
}
@keyframes i {
  to{--i: 0}
}
input[type="range" i]::-webkit-slider-thumb{
  view-timeline: --thumb-view inline;
}
```

Adjust the slider on the left to control the `font-size`

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="yLdeEqa" data-pen-title="Fluid typography with slider (CSS-only)" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yLdeEqa">
  Fluid typography with slider (CSS-only)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>