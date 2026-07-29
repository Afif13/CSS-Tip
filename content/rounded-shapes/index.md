---
layout: layouts/post.njk
title: A New Way to Round the Corners of CSS Shapes
description: Learn how to round the corners of any shape with a simple code
date: 2026-07-29
tags: posts
---

The `polygon()` value of `clip-path` accepts a new (optional) corner-rounding parameter that allows you to create curved and rounded shapes easily!

{% image "./image.png", "CSS-only rounded shapes" %}

The code is as simple as the one below.

```css
.shape {
  clip-path: polygon(round 20px, /* your shape */);
}
```

You can also specify a very large value to achieve maximum rounding of the shape. Each corner has a maximum value that you cannot round above. The logic is the same as with `border-radius` for creating circles or pills.

```css
.shape {
  clip-path: polygon(round 9e9px, /* your shape */);
  /* OR  */
  clip-path: polygon(round calc(infinity * 1px), /* your shape */);
}
```

⚠️ Chromium-only for now ⚠️

<p class="codepen" data-height="550" data-pen-title="Rounding CSS Shapes using polygon()" data-preview="true" data-default-tab="result" data-slug-hash="OPWaVjM" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/OPWaVjM">
  Rounding CSS Shapes using polygon()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Until better support, we can still use other techniques, such as mask combined with gradients or `shape()`. Find most of the shapes within [my online collection](https://css-shape.com/).