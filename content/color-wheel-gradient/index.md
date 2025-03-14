---
layout: layouts/post.njk
title: A color wheel with gradient
description: Use the new color interpolation to create a color wheel using conic-gradient()
date: 2023-04-03
tags: posts
---

Use `conic-gradient()` and the new color interpolation to create a nice color wheel 🤩

{% image "./color-wheel.png", "A color wheel made conic-gradient" %}

```css
.box {
  background: conic-gradient(in hsl longer hue,red 0 100%);
}
```

✅ Tell the browser to take the longer route between red and red

❌ No complex color combination


<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="XWPvgZo" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWPvgZo">
  Color wheel</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

