---
layout: layouts/post.njk
title: A Modern way to create octagon shapes
description: Two lines of CSS code an no magic number for an octagon shape
date: 2024-01-16
tags: posts
---

An easy and modern way to create Octagon shapes
* Only 2 CSS declarations
* No magic numbers
* A 4-point polygon (instead of 8) for the clip-path


{% image "./image.png", "CSS-only octagon shapes" %}

```css
.octa {
  width: 200px;
  
  aspect-ratio: 1;
  --o:calc(50%*tan(-22.5deg));
  clip-path: polygon(
    var(--o) 50%,50% var(--o),
    calc(100% - var(--o)) 50%,
    50% calc(100% - var(--o))
  );
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="LYaxqEg" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/LYaxqEg">
  CSS-only octagon shapes (the modern way)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
