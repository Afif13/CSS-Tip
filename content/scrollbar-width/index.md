---
layout: layouts/post.njk
title: Get the width of the scrollbar using only CSS
description: Using modern CSS features to get the scrollbar width as a CSS variable
date: 2024-07-31
tags: posts
---

"What is the width of the scrollbar?" A question we can answer using a few lines of modern CSS! No need for JavaScript and you get the value as a CSS variable defined at `:root` level. 

```css
@property --x {
  syntax: "<number>";
  inherits: true;
  initial-value: 1;
}
html {
  /* --w will contain a unitless value of the scrollbar width */
  --w: calc(100cqw*var(--x)/1px);
  timeline-scope: --x;
  animation: --x linear;
  animation-timeline: --x;
  animation-range: entry 100% exit 100%;
}
html:before {
  content: "";
  position: fixed;
  left: 0;
  aspect-ratio: 1;
  overflow: hidden;
  scrollbar-gutter: stable;
  view-timeline: --x inline;
}
@keyframes --x {to {--x:0}}
```

Chrome-only for now

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="rNEjyNj" data-pen-title="CSS-only scrollbar width" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/rNEjyNj">
  CSS-only scrollbar width</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [frontendmasters.com/blog/how-to-get-the-width-height-of-any-element-in-only-css](https://frontendmasters.com/blog/how-to-get-the-width-height-of-any-element-in-only-css/)

Related: [https://codepen.io/propjockey/pen/ogzovYg](https://codepen.io/propjockey/pen/ogzovYg)