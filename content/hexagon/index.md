---
layout: layouts/post.njk
title: The future of hexagon shapes
description: A new way to easily create hexagon shapes using corner-shape
date: 2025-06-12
tags: posts
---

A new and easy way to create hexagon shapes using `corner-shape`. As a bonus, you can add a border to it.

It's the only method that works with borders!


{% image "./image.png", "CSS-only hexagon shapes using corner-shape" %}

```css
.hexagon {
  border-radius: 50% / 25%;
  corner-shape: bevel;
  aspect-ratio: cos(30deg);
  border: 8px solid purple; /* the border will follow the shape! */
}
/* OR  */
.hexagon {
  border-radius: 25% / 50%;
  corner-shape: bevel;
  aspect-ratio: 1/cos(30deg);
  border: 8px solid purple; /* the border will follow the shape! */
}
```

⚠️ Very limited support (Chrome-only with experimental flag enabled) ⚠️

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="yyNjgzR" data-pen-title="Hexagon shapes (with border!)" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yyNjgzR">
  Hexagon shapes (with border!)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Until better support use this: [A Modern way to create hexagon shapes](/hexagon-shape/)