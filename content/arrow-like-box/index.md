---
layout: layouts/post.njk
title: Arrow-like Box with rounded corners
description: Using modern CSS to create a rectangle with a rounded triangle shape on one side
date: 2025-04-22
tags: posts
---

Another experimentation using the new `shape()` function to add rounded corners to a box with a triangular shape.

{% image "./image.png", "A CSS-only arrow-like rectangle" %}

A complex-looking code but all you have to do is to update a few variables.

```css
.box {
  --h: 200px; /* element height */
  --s: 90px;  /* triangle size */
  --r: 10px;  /* radius */
  
  height: var(--h);
  border-radius: var(--r) 0 0 var(--r);
  --_a: atan2(var(--s),var(--h)/2);
  clip-path: 
   shape(from 0 0,
    line  to calc(100% - var(--s) - var(--r)) 0,
    curve to calc(100% - var(--s) + var(--r)*sin(var(--_a))) 
             calc(var(--r)*cos(var(--_a)))
    with calc(100% - var(--s)) 0,
    line  to calc(100% - var(--r)*sin(var(--_a))) 
             calc(50%  - var(--r)*cos(var(--_a))),
    curve to calc(100% - var(--r)*sin(var(--_a)))
             calc(50%  + var(--r)*cos(var(--_a))) 
    with 100% 50%,
    line  to calc(100% - var(--s) + var(--r)*sin(var(--_a))) 
             calc(100% - var(--r)*cos(var(--_a))),
    curve to calc(100% - var(--s) - var(--r)) 100%
    with calc(100% - var(--s)) 100%,
    line to 0 100%
   );
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="LEENyEq" data-pen-title="Rounded Triangle Boxes" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/LEENyEq">
  Rounded Triangle Boxes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

