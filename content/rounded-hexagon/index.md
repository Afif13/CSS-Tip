---
layout: layouts/post.njk
title: Hexagon shapes with rounded corners
description: Use the new shape() function to create a hexagon shape with rounded corners
date: 2025-04-16
tags: posts
---

We can create [a hexagon shape](/hexagon-shape/) using `clip-path: polygon()` but what about the rounded corners variation? It's now possible with the new `clip-path: shape()`. The code is more complex but you can easily control it using CSS variables.

{% image "./image.png", "CSS-only hexagon shape with rounded corners" %}


```css
.hexagon {
  --r: 0.15; /* control the radius [0 1] */
  --a: 30deg; /* control the rotation */
  
  width: 280px;
  aspect-ratio: 1;
  clip-path: shape(/* a complex code but all you have to do is to update the above variables */);
}
```

As a bonus we can animate the radius and also rotate the shape. Here is a demo with a cool hover effect.

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="myydVbr" data-pen-title="Rounded hexagon shapes with hover effect" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/myydVbr">
  Rounded hexagon shapes with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

⚠️ Chrome-only for now ⚠️
