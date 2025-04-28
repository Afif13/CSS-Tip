---
layout: layouts/post.njk
title: A heart shape with modern CSS
description: Use the new shape() function to create a heart shape with minimal code
date: 2025-04-23
tags: posts
---

Another classic shape made easy with the new `shape()` function. A heart shape with a simple code.

{% image "./image.png", "CSS-only heart shape" %}

```css
.heart {
  aspect-ratio: 1;
  clip-path: 
    shape(
      from 50% 91%,
      line to 90% 50%,
      arc to 50% 9%  of 1%,
      arc to 10% 50% of 1%
    );
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="LEEbdrw" data-pen-title="Heart shape using shape()" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/LEEbdrw">
  Heart shape using shape()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

For better support check this: [Turn your image into a heart](/image-heart-shape/)