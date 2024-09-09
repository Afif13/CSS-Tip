---
layout: layouts/post.njk
title: Dashed lines using CSS gradient
description: Ceate dashed lines using one gradient and CSS variables
date: 2022-07-13
tags: posts
---

Create dashed lines using only one gradient


{% image "./dashes.png", "A background with dashed lines" %}

```css
html {
  --c: #333; /* color */
  --t: 2px;  /* thickness of the lines */
  --g: 50px; /* gap between lines */
  --s: 12px; /* size of the dashes*/
  
  background:
    conic-gradient(at var(--t) 50%,#0000 75%,var(--c) 0)
    var(--g)/calc(var(--g) + var(--t)) var(--s);
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="XWEjYgZ" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWEjYgZ">
  CSS Only dashed lines</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

