---
layout: layouts/post.njk
title: Three Shape Variations using border-shape
description: Use border-shape to create any shape, its border-only and cutout variations
date: 2026-05-19
tags: posts
---

Using `shape()`, you can easily create any [CSS-only shapes](https://css-shape.com/), and if you combine it with `border-shape`, you can have the border-only and cutout variations using almost the same code structure.

{% image "./image.png", "CSS shape, border-only and cutout version" %}

You can get the main shape by simply using `border-shape` and background:

```css
.shape {
  border-shape: shape(/* you shape code */);
  background: #c1121f; /* you can also have a gradient  */
}
```

To get the border-only version, you use border instead of background:

```css
.border-only {
  border-shape: shape(/* you shape code */);
  border: 10px solid #c1121f;
}
```

To get the cutout version, add `inset(0)` to the previous code.

```css
.cutout {
  border-shape: inset(0) shape(/* you shape code */);
  border: 10px solid #c1121f;
}
```

`border-shape` accepts two shape values. In such a case, the border is rendered as the area between the two shapes. The first value defines the outer boundary, and the second value defines the inner boundary. By making the first shape a rectangle using `inset(0)`, we get the cutout version!

{% image "./image1.png", "cutout shape using border-shape" %}

⚠️ It's Chrome-only for now ⚠️

<p class="codepen" data-height="400" data-pen-title="Three shape variations using border-shape" data-preview="true" data-default-tab="result" data-slug-hash="dPOvVRb" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dPOvVRb">
  Three shape variations using border-shape</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Until better support, you can achieve the same using `clip-path` (except for the border-only version): [Invert CSS Shapes using shape()](https://css-tip.com/invert-shape/)
