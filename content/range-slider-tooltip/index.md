---
layout: layouts/post.njk
title: Custom range slider with tooltip
description: Using modern CSS features to create a fancy range slider with tooltop
date: 2024-06-04
tags: posts
---

Create a custom range slider with a tooltip showing the selected value. There is no JS to update the values, it's pure CSS with minimal HTML!

{% image "./image.png", "CSS-only range slider with tooltip" %}

```html
<label>
  <input type="range" id="one" min="0" max="120" step="1" value="20">
  <output for="one" style="--min: 0;--max: 120"></output>
</label>
```

Powered by modern CSS features:
* Scroll Driven animation
* Anchor positioning
* `@property` & CSS variables


The support for the tooltip feature is still limited (chrome-only for now) but the range slider works fine in all the browsers.

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="JjqNEbZ" data-pen-title="CSS-only Custom range slider" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/JjqNEbZ">
  CSS-only Custom range slider</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>