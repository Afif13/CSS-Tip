---
layout: layouts/post.njk
title: Input Range Slider with Custom Shapes
description: Using modern CSS features to apply fancy shapes to native range sliders
date: 2026-10-19
tags: posts
---

Building on a [previous idea](/wiggly-range-slider/), here is a more generic implementation of range sliders with custom shapes and tooltips. No JavaScript and a lot of cool CSS features (`border-shape`, `shape()`, Scroll-Driven Animations, `@property`, etc.)

{% image "./image.png", "CSS-only input range slider with custom shape" %}

Minimal HTML:

```html
<label>
  Fancy Range Slider
  <input type="range" id="one" min="0" max="100" step="1" value="20">
  <output for="one" min="0" max="100"></output>
</label>  
```

And CSS variables to easily control everything:

```css
label:has(input[type=range]) {
  --c: #BD1550; /* slider color */
  --g: 5px; /* the gap */
  --l: 6px; /* line thickness */
  --t: 45px; /* size of the thumb*/
  --s: 120px; /* size/height of the slider */
  --p: shape(...)  /* the shape of the slider */
}
```

⚠️ A Chromium-only experience ⚠️

<p class="codepen" data-theme-id="39604" data-height="600" data-pen-title="Custom shape range slider" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="emvrrvm" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a150b9-e78d-71ee-9dea-3adfe3e18538">
  Custom shape range slider</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>
