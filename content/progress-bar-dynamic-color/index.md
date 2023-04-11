---
layout: layouts/post.njk
title: Progress bar with dynamic coloration
description: Create a scrolling shadow effect using only CSS gradients
date: 2021-11-15
tags: posts
---

Create a CSS-only progress bar with a dynamic coloration. The color change based on the value 
* No JavaScript 
* No specific CSS selector

{% image "./image.png", "progress bar with dynamic coloration" %}


```css
progress[value] {
  --w:200px; /* The width */
  /* The background property */
  --b: /* static layers */
      linear-gradient(#fff8,#fff0),
      repeating-linear-gradient(135deg,#0003 0 10px,#0000 0 20px),
      /* dynamic layers */
      /* if < 30% "red" */
      linear-gradient(red    0 0) 0 /calc(var(--w)*.3 - 100%) 1px,
      /* if < 60% "orange" */
      linear-gradient(orange 0 0) 0 /calc(var(--w)*.6 - 100%) 1px,
      /* else "green" */
      green;
  width: var(--w); 
  height: 20px;
  background-color: lightgrey;
  border-radius: 50px;
}
progress[value]::-webkit-progress-bar {
  background-color: lightgrey;
  border-radius: 50px;
}
progress[value]::-webkit-progress-value {
  border-radius: 50px;
  background:var(--b);
}
progress[value]::-moz-progress-bar {
  border-radius: 50px;
  background:var(--b);
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="dyzgwOa" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dyzgwOa">
  Progress bar with dynamic colors</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>