---
layout: layouts/post.njk
title: Smooth rotation with modern CSS
description: Create a smooth rotation of any element using modern CSS
date: 2025-01-03
tags: posts
---

Use modern CSS to control the rotation of any element smoothly. Hover to rotate, click to accelerate, unhover to return to the initial position following the shortest path!
* Single element (no pseudo-element)
* No keyframes
* Powered by `@property` and math functions

{% image "./image.png", "CSS-only smooth rotation" %}

```css
@property --a {
  syntax: "<angle>";
  inherits: false;
  initial-value: 0deg; 
}
@property --i {
  syntax: "<number>";
  inherits: false;
  initial-value: 0; 
}
@property --j {
  syntax: "<number>";
  inherits: false;
  initial-value: 1; 
}
.box {
  --t: 1turn; /* control the modulo (the smallest angle after which you get back to the same visual) */
  --d: .8s;   /* the transition when you unhover */

  rotate: calc(mod(var(--a),var(--t)/2)*var(--i) + clamp(var(--t)/-2*var(--i),(var(--t)/2 - mod(var(--a),var(--t)))*9999,0deg));
  transition: --i var(--d),--a 0s var(--d),--j var(--d);
}
.box:hover {
  --i: 1;
  --a: calc(15turn*var(--j));
  transition: --i 0s,--a 30s linear,--j .5s;
}
.box:active {
  --j: 2; /* control the speed on click [1 infinity[ */
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="azoVpzN" data-pen-title="Hover to rotate, click to accelerate, unhover for a smooth stop!" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/azoVpzN">
  Hover to rotate, click to accelerate, unhover for a smooth stop!</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>