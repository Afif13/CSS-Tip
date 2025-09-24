---
layout: layouts/post.njk
title: Sequential Animations with N elements
description: A simple CSS code to animate different elements sequentially
date: 2025-08-07
tags: posts
---

Using modern CSS, you can create a sequential animation that involves an unknown number of items with a simple code. No need for complex keyframes, delays, or magic numbers. A clever combination of [the `sibling-index()`/`sibling-count()` functions](/element-index/) and `linear()` will do the job!


{% image "./image.png", "CSS-only sequential animations" %}

```html
<div class="container">
  <div></div>
  <div></div>
  <div></div>
  <!-- as many elements as you want -->
</div>
```

```css
.container > * {
  --d: .5s; /* animation duration */
  
  --_s: calc(100%*(sibling-index() - 1)/sibling-count());
  --_e: calc(100%*(sibling-index())/sibling-count());
  animation: x calc(var(--d)*sibling-count()) infinite linear(0,0 var(--_s),1,0 var(--_e),0);
}
@keyframes x {
  to {
    scale: .8;
  }
}
```

⚠️ Limited support (Chrome only for now) ⚠️

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="dPYRzKq" data-pen-title="Sequential Animations" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dPYRzKq">
  Sequential Animations</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>
