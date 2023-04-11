---
layout: layouts/post.njk
title: One column to control the height of another
description: Make one height control the height of another
date: 2021-11-05
tags: posts
---

Make one column control the height of another column whatever its content. 

Below, the left column will control the right column.

No JavaScript is needed, only three lines of CSS will do the job

{% image "./image.png", "equal height column" %}


```css
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
.grid .left {/*nothing here*/}
.grid .right {
  height: 0;
  min-height: 100%;
  overflow: auto;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="poraqNz" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/poraqNz">
  CSS grid - dynamic columns</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [dev.to/afif/responsive-text-based-on-image-size-36n9](https://dev.to/afif/responsive-text-based-on-image-size-36n9)