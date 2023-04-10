---
layout: layouts/post.njk
title: A CSS-only Zig-Zag edge
description: Use CSS mask to create an easy to adjust Zig-Zag edge/border
date: 2022-09-02
tags: posts
---

How much code is needed to create a Zig-Zag edge?
* One Property
* One Gradient

Use an online generator to easily get the code: [css-generators.com/custom-borders](https://css-generators.com/custom-borders/)


{% image "./zig-zag-edge.png", "A CSS-only zig-zag border" %}

```css
.zig-zag {
  mask: conic-gradient(from -45deg at bottom,#000 90deg,#0000 0) 50% / 60px 100%;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="VwxwpbB" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/VwxwpbB">
  CSS only Zig-Zag edge</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [css-tricks.com/css-borders-using-masks](https://css-tricks.com/css-borders-using-masks/)