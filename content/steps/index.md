---
layout: layouts/post.njk
title: How to correctly use steps() with animations
description: The default behavior of steps() is not intuitive so learn how to use it correctly
date: 2024-11-18
tags: posts
---

You want to create a discrete animation using `steps()` but you struggle with its value, right? You never know how many steps it requires and it never works as expected!

In most cases, adding an extra value will fix your issue.


```css
/* Don't ❌ */
.element {
  animation: anime 3s steps(3);
}
/* Do  ✅ */
.element {
  animation: anime 3s steps(3,jump-none);
}
```

By default, `steps()` uses `jump-end` which is not very intuitive. The behavior you are looking for is the one of `jump-none`


{% image "./image.png", "Illustrating the steps() function" %}

Here is a demo with some common examples (see the comments in the CSS code)

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="WNVBvNM" data-pen-title="Using steps(N,jump-none)" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/WNVBvNM">
  Using steps(N,jump-none)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>