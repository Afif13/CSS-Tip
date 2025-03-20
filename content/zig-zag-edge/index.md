---
layout: layouts/post.njk
title: Zig-Zag edges using CSS mask
description: One line of code to add Zig-Zag edges to any element using the mask property
date: 2025-03-20
tags: posts
---

Add Zig-Zag edges to your element using the `mask` property and one gradient.

{% image "./image.png", "zig-zag edges using mask" %}

```css
.zig-zag {
  --s: 30px;  /* control the size (height of the spikes) */
  --a: 90deg; /* control the angle */
  
  mask: 
    repeating-conic-gradient(from calc(180deg - var(--a)/2) at 50% var(--s),#000 0 var(--a),#0000 0 180deg) 
    50% calc(-1*var(--s))/calc(2*var(--s)*tan(var(--a)/2));
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="QwWmXPw" data-pen-title="Zig-Zag edges" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/QwWmXPw">
  Zig-Zag edges</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Use my online generator to get the code of the different variations: [css-generators.com/custom-borders](https://css-generators.com/custom-borders/)


{% image "./image2.png", "CSS-only zig-zag borders" %}


More detail: [css-tricks.com/css-borders-using-masks](https://css-tricks.com/css-borders-using-masks/)