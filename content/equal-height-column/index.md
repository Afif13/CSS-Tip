---
layout: layouts/post.njk
title: One column to control the height of another 
description: Make one column control the height of another one with a simple property
date: 2021-11-05
tags: posts
---

Make one column control the height of another column whatever its content using the `contain` prorperty. No JavaScript is needed.

Below, the right column will follow the height of the left column.


{% image "./image.png", "CSS-only equal height column" %}


```css
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
.grid .right {
  contain: size; /* Disable the size contribution of the content inside the right column */
}
.grid .left {
  /* nothing here */
}
```

We can also replace `contain: size` with the below:

```css
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
.grid .right {
  height: 0; /* No size contribution */
  min-height: 100%; /* force the element to be full height after size calculation */
}
.grid .left {
  /* nothing here */
}
```


<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="poraqNz" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/poraqNz">
  CSS grid - dynamic columns</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

