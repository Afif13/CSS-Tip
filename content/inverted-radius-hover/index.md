---
layout: layouts/post.njk
title: Inverted radius shape with hover effect
description: An inverted border-radius shape with a fancy reveal animation on hover
date: 2025-01-29
tags: posts
---

Combining the [inverted radius shape](https://css-shape.com/inverted-radius/) with modern CSS to create a fancy reveal animation. Hover the image to reveal the text.
* Minimal HTML (the `<figure>` element)
* Powered by `@property` and CSS Mask
* Optimized with CSS variables

{% image "./image.png", "CSS-only inverted radius shape" %}

```css
@property --_x {
  syntax: "<length>";
  inherits: true;
  initial-value: 0px; 
}
figure {
  --w: 280px; /* image width */
  --r: .5em;  /* radius */
  
  display: grid;
  place-items: end end;
  font: bold 40px/1.5 monospace;
  transition: --_x .5s;
}
figure > * {
  grid-area: 1/1;
}
figure:hover {
  --_x: calc(var(--w) - 3*var(--r) - .5lh);
}
figure img {
  width: var(--w);
  aspect-ratio: 1;
  border-radius: var(--r);
  --_m:/calc(2*var(--r)) calc(2*var(--r)) radial-gradient(#000 69%,#0000 72%);
  --_g:conic-gradient(from 90deg at calc(100% - var(--r)) calc(100% - var(--r)),#0000 25%,#000 0);
  --_d:(.5lh + var(--r));
  mask:
    calc(100% - var(--_d) - var(--_x)) 100% var(--_m),
    100% calc(100% - var(--_d)) var(--_m),
    radial-gradient(.5lh at 100% 100%,#0000 99%,#000 calc(100% + 1px)) 
     calc(-1*var(--r) - var(--_x)) calc(-1*var(--r)),
    var(--_g) calc(-1*var(--_d) - var(--_x)) 0,
    var(--_g) 0 calc(-1*var(--_d));
  mask-repeat: no-repeat; 
}
figure figcaption {
  height: 1lh;
  width: calc(1lh + var(--_x)); 
  box-sizing: border-box;
  translate: calc(.5lh - var(--r)) calc(.5lh - var(--r));
  overflow: hidden;
  border-inline: calc(.5lh - .5ch) solid #0000;
  clip-path: inset(5px round 1lh);
}
```
<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="zxOeWqV" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zxOeWqV">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>