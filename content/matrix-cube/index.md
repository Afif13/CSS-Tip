---
layout: layouts/post.njk
title: A matrix of cubes using one element
description: Create a matrix of cubes using only one element
date: 2022-01-03
tags: posts
---

Create a [matrix of cubes](https://css-shape.com/matrix-cubes/) using only one element. Yes it's possible!


{% image "./cube.png", "A matrix of cube" %}


```css
.cube {
  --m: 4; /* number of columns */
  --n: 5; /* number of rows */
  --size: 40px; /* size of the cubes */
  --gap :10px;  /* gap between cubes */

  aspect-ratio: var(--m)/var(--n);
  width: calc(var(--m)*(1.353*var(--size) + var(--gap)));
  background:
    conic-gradient(from -90deg at var(--size) calc(0.353*var(--size)),
      #249FAB 135deg,#81C5A3 0 270deg,#26609D 0) /* update the colors here */
    0 0/calc(100%/var(--m)) calc(100%/var(--n));
  mask:
    linear-gradient(to bottom right,
       #0000 calc(0.25*var(--size)),#000 0 calc(100% - calc(0.25*var(--size)) - 1.414*var(--gap)),#0000 0),
    conic-gradient(from -90deg at right var(--gap) bottom var(--gap),#000 90deg,#0000 0);
  mask-size: calc(100%/var(--m)) calc(100%/var(--n));
  mask-composite: intersect;
}
```


<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="PoJeqwN" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/PoJeqwN">
  matrix of cube with one element</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More CSS Shapes: [css-shape.com](https://css-shape.com)