---
layout: layouts/post.njk
title: Equal width buttons to the widest one
description: A few lines of code ot create equal width buttons.
date: 2022-01-20
tags: posts
---

Make a set of buttons equal in width to the widest one using a few lines of code.
* No JavaScript
* Works with any number of button
* Easily switch between the horizontal and vertical configuration

{% image "./image.png", "eqaul width buttons" %}

```css
.container {
  display: inline grid;
  grid-auto-flow: column; /* OR row */
  grid-auto-columns: 1fr;
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="OJxYvJg" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/OJxYvJg">
  Equal width buttons</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>