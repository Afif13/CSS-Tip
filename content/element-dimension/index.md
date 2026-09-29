---
layout: layouts/post.njk
title: Get the width & height of any element without JavaScript
description: Using modern CSS to get the size of any element as CSS variables
date: 2024-07-26
tags: posts
---

Use Scroll-Driven Animations and modern CSS features to get the width and height of any element without JavaScript. You get unitless pixel values as CSS variables that you can make available anywhere on the page.

```css
@property --_x {syntax: "<number>";inherits: true;initial-value: 0;}
@property --_y {syntax: "<number>";inherits: true;initial-value: 0;}

.size {
  overflow: auto;
  position: relative;
  --w: round(1/var(--_x)); /* element width */
  --h: round(1/var(--_y)); /* element height */
  timeline-scope: --cx,--cy;
  animation: x linear,y linear;
  animation-timeline: --cx,--cy;
  animation-range: entry 100% exit 100%; 
}
.size:before {
  content: "";
  position: absolute;
  left: 0;
  top: 0;
  width: 1px;
  aspect-ratio: 1;
  view-timeline: --cx inline,--cy block;
}
@keyframes x {0% {--_x:1}}
@keyframes y {0% {--_y:1}}
```

Resize the below demo to see how the values update in real-time:

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="MWMyYeP" data-pen-title="Get width/height of elements using CSS" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/MWMyYeP">
  Get width/height of elements using CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Here is the particular case of the screen sizes

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="eYwZgqL" data-pen-title="Get screen dimension using only CSS" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/eYwZgqL">
  Get screen dimension using only CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [frontendmasters.com/blog/how-to-get-the-width-height-of-any-element-in-only-css](https://frontendmasters.com/blog/how-to-get-the-width-height-of-any-element-in-only-css/)