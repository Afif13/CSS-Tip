---
layout: layouts/post.njk
title: Update CSS variables using range slider
description: A CSS-only way to update CSS variables in real time using range slider
date: 2024-09-16
tags: posts
---

Using scroll-driven animations, you can link a CSS variable with a range slider and easily update its value!

No more JavaScript to do this. A few lines of CSS, one HTML element and you can update any value in real time.


```css
@property --_f {
  syntax: "<number>";
  inherits: true;
  initial-value: 0; 
}
:root {
  --font-size-min: 12px; /* define the min */
  --font-size-max: 64px; /* define the max */
  /* the variable you will be using */
  --font-size: calc(
      var(--font-size-max)*var(--_f) +
      var(--font-size-min)*(1 - var(--_f))
    );
/* No need to touch the below
   Yes, you can use --_f everywhere
*/
  timeline-scope: --_f;
  animation: var(--_f) linear both;
  animation-timeline: --_f;
  animation-range: entry 100% exit 0%;
}
@keyframes --_f {0%{--_f: 1}}

input[type="range"] { overflow: hidden; }
input[type="range"]::-webkit-slider-thumb{ 
  view-timeline: --_f inline;
}
/* --- */

p {
  font-size: var(--font-size);
}
```
Here is a demo where you can update three different variables (chrome-only for now)

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="GRbawQm" data-pen-title="Update CSS variables using range slider (CSS-only)" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/GRbawQm">
  Update CSS variables using range slider (CSS-only)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
