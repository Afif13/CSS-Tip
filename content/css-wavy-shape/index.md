---
layout: layouts/post.njk
title: A CSS-only wavy shapes
description: Combine gradients and CSS mask to create a wavy shape with a little of code
date: 2022-09-29
tags: posts
---

How much code is needed to create a Wavy Shape?
* 1 Property
* 2 Gradients

Use an online generator to easily get the code: [css-generators.com/wavy-shapes](https://css-generators.com/wavy-shapes/)

{% image "./wavy-shape.png", "A wavy shape" %}

```css
.wave {
  --s: 50px; /* the size of the wave */
  --p: .6;   /* the curvature of the wave [0 2] */

  --R: calc(var(--s)*sqrt(var(--p)*var(--p) + 1)) at 50%;
  mask:
    radial-gradient(var(--R) calc(100% - var(--s)*(1 + var(--p))), #000 99%, #0000 101%) 
      calc(50% - 2*var(--s)) 0/calc(4 * var(--s)),
    radial-gradient(var(--R) calc(100% + var(--s)*var(--p)), #0000 99%, #000 101%) 
      50% calc(-1*var(--s))/calc(4 * var(--s)) repeat-x;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="qBYxzMj" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/qBYxzMj">
  CSS only wavy shape</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More detail: [css-tricks.com/how-to-create-wavy-shapes-patterns-in-css](https://css-tricks.com/how-to-create-wavy-shapes-patterns-in-css/)