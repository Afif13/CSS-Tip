---
layout: layouts/post.njk
title: "A Squircle Shape using clip-path: shape()"
description: Using the shape() function to approximate the classic squircle shape
date: 2026-03-05
tags: posts
---

Until better support for `corner-shape`, we can approximate a squircle shape using `clip-path: shape()`. A flexible implementation using CSS variable to easily control the radius.


{% image "./image.png", "CSS-only squircle shape" %}

```css
.squircle {
  --r: 50%; /* between 0% (square) and 50% (squircle) (You can also use pixel value) */
  
  --_r: clamp(0%,var(--r)/2,25%);
  --_v: calc(var(--_r)*(1 - sqrt(2)/4));
  --_p: calc(var(--_v) - var(--_r)/2);
  clip-path: shape(
    from var(--_v) var(--_p),
    curve to 50% 0 with var(--_r) 0,
    curve to calc(100% - var(--_v)) var(--_p) with calc(100% - var(--_r)) 0,
    curve to calc(100% - var(--_p)) var(--_v) with calc(100% - 2*var(--_p)) calc(2*var(--_p)),
    curve to 100% 50% with 100% var(--_r),
    curve to calc(100% - var(--_p)) calc(100% - var(--_v)) with 100% calc(100% - var(--_r)),
    curve to calc(100% - var(--_v)) calc(100% - var(--_p)) with calc(100% - 2*var(--_p)) calc(100% - 2*var(--_p)),
    curve to 50% 100% with calc(100% - var(--_r)) 100%,
    curve to var(--_v) calc(100% - var(--_p)) with var(--_r) 100%,
    curve to var(--_p) calc(100% - var(--_v)) with calc(2*var(--_p)) calc(100% - 2*var(--_p)),
    curve to 0 50% with 0 calc(100% - var(--_r)),
    curve to var(--_p) var(--_v) with 0 var(--_r),
    curve to var(--_v) var(--_p) with calc(2*var(--_p)) calc(2*var(--_p))
  );
}
```

In the demo below, you can adjust the radius and compare the `shape()` implementation with the `corner-shape` one. 

<p class="codepen" data-height="480" data-pen-title="Squircle (shape() vs corner-shape)" data-preview="true" data-default-tab="result" data-slug-hash="KwgVxRZ" data-user="t_afif" style="height: 480px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/KwgVxRZ">
  Squircle (shape() vs corner-shape)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

You can also generate the code using my [fancy frame generator](https://css-generators.com/fancy-frame/) by reducing the granularity and making the frame size equal to `0`.

{% image "./image1.png", "Generator for squircle shape" %}