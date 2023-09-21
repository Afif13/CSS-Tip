---
layout: layouts/post.njk
title: Rotated Ribbon Shape with hover effect
description: a fancy ribbon shape with a nice hover effect
date: 2023-09-21
tags: posts
---

Place your title into a fancy Ribbon Shape with a cool hover effect 😍
* Only one element
* Optimized with CSS variables
* Powered by modern CSS features 💪


{% image "./image.png", "A CSS-only ribbon shape" %}

```css
@property --a {
  syntax: "<angle>";
  initial-value: 0deg;
  inherits: true;
}

h1 {
  --r: 30px;  /* control the cutout of the ribbon */
  --a: 15deg; /* control the angle (only positive values) */
  --c: #d81a14;
  
  line-height: 1.6; /* this will control the height */
  padding-inline: .5lh; 
  color: #fff;
  background:
    linear-gradient(calc(90deg + var(--a)),
      #0000 calc(1lh*sin(var(--a)) - 1px),
      var(--c) calc(1lh*sin(var(--a))) calc(100% - 1lh*sin(var(--a))),
      #0000 calc(100% - 1lh*sin(var(--a)) + 1px)
    );
  position: relative;
  rotate: calc(-1*var(--a));
  transform-style: preserve-3d;
  transition: --a .5s;
  cursor: pointer;
}
h1:before,
h1:after{
  content: "";
  position: absolute;
  transform: translate3d(0,0,-1px);
  rotate: var(--a);
  height: calc(1lh/cos(var(--a)));
  width: calc(100%*cos(var(--a)) - 1lh*sin(var(--a))) ;
  background: color-mix(in srgb,var(--c),#000 40%);
  pointer-events: none;
}
h1:before {
  right: 0;
  top: 0;
  transform-origin: top right;
  clip-path: polygon(0 0,100% 0,100% 100%,0 100%,var(--r) 50%);
}
h1:after {
  left: 0;
  bottom: 0;
  transform-origin: bottom left;
  clip-path: polygon(0 0,100% 0,calc(100% - var(--r)) 50%,100% 100%,0 100%);
}
h1:hover {
  --a: 0deg;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="ZEVvzKG" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZEVvzKG">
  Rotated Ribbon with a cool hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More Ribbon Shapes: [css-generators.com/ribbon-shapes](https://css-generators.com/ribbon-shapes/)