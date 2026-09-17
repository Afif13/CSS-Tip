---
layout: layouts/post.njk
title: Complex border-only Shapes with Gradient Coloration
description: Using border-shape with border-area to easily create border-only shapes
date: 2026-09-17
tags: posts
---

You can combine [`border-shape`](/border-shape/) and [`border-area`](/background-clip/) to easily border-only shapes with gradient coloration easily. No more hacks or complex code, just 3 lines and you're done!

{% image "./image.png", "Border-only shapes with gradient coloration" %}

```css
.shape-gradient {
  border: 10px solid #0000; /* a transparent border */
  border-shape: shape() | polygon() | etc; /* the  shape */
  background: linear-gradient(#0077b6,#f4a261) border-area; /* gradient + border-area */
}
```

⚠️ Chromium-only for now ⚠️

<p class="codepen" data-height="450" data-pen-title="Complex border-only gradient shapes" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="PwpbMqy" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a0aea9-0880-76c4-a70f-eb3f996d10f6">
  Complex border-only gradient shapes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

