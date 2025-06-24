---
layout: layouts/post.njk
title: Dots loader using shape()
description: A classic 3 dots loader created using the new shape()
date: 2025-06-24
tags: posts
---

Recreating a 3 dots loader using `shape()` and animating it using CSS variables and `@property`

{% image "./image.png", "CSS-only dots loader" %}

```css
@property --x {
  syntax: "<percentage>";
  inherits: false;
  initial-value: 80%; 
}
@property --y {
  syntax: "<percentage>";
  inherits: false;
  initial-value: 80%; 
}
@property --z {
  syntax: "<percentage>";
  inherits: false;
  initial-value: 80%; 
}
.loader {
  aspect-ratio: 3;
  --d: ,arc by 0 -60% of 1px, arc by 0 60% of 1px;
  clip-path: 
    shape(
      from    calc( 50%/3) var(--x) var(--d),
      move to calc(150%/3) var(--y) var(--d),
      move to calc(250%/3) var(--z) var(--d)
    );
  animation: l 1s infinite;
}
@keyframes l {
  20%  {--x:60%; --y:80%;         }
  40%  {--x:100%;--y:60%; --z:80% }
  60%  {--x:80%; --y:100%;--z:60% }
  80%  {         --y:80%; --z:100%}
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="azOPoaO" data-pen-title="Dots loader using shape()" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/azOPoaO">
  Dots loader using shape()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

More CSS Loaders: [css-loaders.com](https://css-loaders.com/)