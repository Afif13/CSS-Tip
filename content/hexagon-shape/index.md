---
layout: layouts/post.njk
title: A Modern way to create hexagon shapes
description: Two lines of CSS code an no magic number for an hexagon shape
date: 2024-01-11
tags: posts
---

An easy and modern way to create Hexagon Shapes
* Only 2 CSS declarations
* No magic numbers
* A simple 4-point polygon for the clip-path


{% image "./image.png", "CSS-only hexagon shapes" %}

```css
.hex {
  aspect-ratio: 1/cos(30deg);
  clip-path: polygon(50% -50%,100% 50%,50% 150%,0 50%);
}

.hex-alt {
  aspect-ratio: cos(30deg);
  clip-path: polygon(-50% 50%,50% 100%,150% 50%,50% 0);
  /* Notice how I simply switched the x/y 
     of the previous polygon, easy! */
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="KKEMjxV" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/KKEMjxV">
  CSS-only hexagon shapes (the modern way)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More CSS Shapes: [css-shape.com](https://css-shape.com)