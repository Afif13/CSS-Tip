---
layout: layouts/post.njk
title: A CSS-only wavy divider
description: Use modern CSS and few lines of code to create a cool divider
date: 2024-03-29
tags: posts
---

Use modern CSS and add a cool Wavy divider to your section. Only one property and two gradients are needed.

{% image "./image.png", "CSS-only wavy divider" %}

```css
.wavy {
  --s: 1.6em; /* the size of the wave */
  --p: .8;    /* the curvature of the wave [0 2] */

  --R: calc(var(--s)*sqrt(var(--p)*var(--p) + 1)) at 50%;
  mask:
    radial-gradient(var(--R) calc(100% - var(--s)*(1 + var(--p))), #000 99%, #0000 101%) 
      calc(50% - 2*var(--s)) 0/calc(4*var(--s)),
    radial-gradient(var(--R) calc(100% + var(--s)*var(--p)), #0000 99%, #000 101%) 
      50% calc(-1*var(--s))/calc(4*var(--s)) repeat-x;
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="RwOLZrL" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/RwOLZrL">
  CSS-only wavy divider</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

You can also get the code from [my online generator](https://css-generators.com/wavy-shapes/).

More detail: [css-tricks.com/how-to-create-wavy-shapes-patterns-in-css](https://css-tricks.com/how-to-create-wavy-shapes-patterns-in-css/)