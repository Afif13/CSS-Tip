---
layout: layouts/post.njk
title: The difference between zoom and scale
description: Learn about the zoom property and how it works
date: 2025-02-17
tags: posts
---

Do you know the `zoom` property? It works the same way as a scale transformation but unlike `scale`, it affects the page layout. In other words, the page layout is recalculated considering the new dimension of the scaled element.


{% image "./image.png", "difference between the zoom property and the scale property" %}


<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="emYpvZN" data-pen-title="Scale vs Zoom" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/emYpvZN">
  Scale vs Zoom</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>