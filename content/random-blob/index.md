---
layout: layouts/post.njk
title: Random Blob Shapes
description: Combining shape() and random() to create unique blob shapes
date: 2026-09-22
tags: posts
---

Creating [CSS Shapes](https://css-shape.com/) is cool, but what about Random CSS Shapes? Thanks to the new `random()` function, we can generate unique shapes. A new shape appears on each page load. You never see the same shape twice.

First off, blob shapes with a cool hover effect!

{% image "./image.png", "CSS-only blob shape" %}

⚠️ Chrome-only with experimental flag enabled ⚠️

<p class="codepen" data-theme-id="39604" data-height="450" data-pen-title="Random Blob Shapes (with hover effect)" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="PwppEgV" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a0c5d3-35c4-7d9e-96cc-151d956fcae5">
  Random Blob Shapes (with hover effect)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

The code is a bit verbose, but one day we will have loops in CSS, and we can optimize it.

```css
.blob {
  --n: 13;  /* if you change this, you need to add more points... we don't have loops in CSS */
  --d: 20%; /* control the depth, can be percentage */

  width: 300px;
  aspect-ratio: 1;
  
  --_r: element-scoped,0px,var(--d);
  --x0: (50% + (50% - random(--0 var(--_r)))*cos(0turn/var(--n)));
  --y0: (50% + (50% - random(--0 var(--_r)))*sin(0turn/var(--n)));
  --x1: (50% + (50% - random(--1 var(--_r)))*cos(1turn/var(--n)));
  --y1: (50% + (50% - random(--1 var(--_r)))*sin(1turn/var(--n)));
  --x2: (50% + (50% - random(--2 var(--_r)))*cos(2turn/var(--n)));
  --y2: (50% + (50% - random(--2 var(--_r)))*sin(2turn/var(--n)));
  --x3: (50% + (50% - random(--3 var(--_r)))*cos(3turn/var(--n)));
  --y3: (50% + (50% - random(--3 var(--_r)))*sin(3turn/var(--n)));
  --x4: (50% + (50% - random(--4 var(--_r)))*cos(4turn/var(--n)));
  --y4: (50% + (50% - random(--4 var(--_r)))*sin(4turn/var(--n)));
  /* etc ... */

  clip-path: shape(
    from      calc((var(--x0 ) + var(--x1 ))/2) calc((var(--y0 ) + var(--y1 ))/2),
    curve  to calc((var(--x1 ) + var(--x2 ))/2) calc((var(--y1 ) + var(--y2 ))/2) with calc(var(--x1)) calc(var(--y1)),
    smooth to calc((var(--x2 ) + var(--x3 ))/2) calc((var(--y2 ) + var(--y3 ))/2),
    smooth to calc((var(--x3 ) + var(--x4 ))/2) calc((var(--y3 ) + var(--y4 ))/2),
    smooth to calc((var(--x4 ) + var(--x5 ))/2) calc((var(--y4 ) + var(--y5 ))/2),
    /* etc .. */
    smooth to calc((var(--x11) + var(--x12))/2) calc((var(--y11) + var(--y12))/2),
    smooth to calc((var(--x12) + var(--x0 ))/2) calc((var(--y12) + var(--y0 ))/2),
    smooth to calc((var(--x0 ) + var(--x1 ))/2) calc((var(--y0 ) + var(--y1 ))/2)
  );
}
```

Until better support, you can get static blob shapes using my online generator: [css-generators.com/blob](https://css-generators.com/blob/)