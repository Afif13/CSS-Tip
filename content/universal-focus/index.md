---
layout: layouts/post.njk
title: The Universal Focus Ring
description: Using anchor positioning to create a fancy focus ring that travels the whole page
date: 2025-11-07
tags: posts
---

Replace the default focus ring with a stylish one that travels between the elements as you navigate with your keyboard. A funny experiment using [Anchor Positioning](/position-area/).

```css
html::after {
  content: "";
  position: fixed;
  position-anchor: --focus;
  inset: anchor(inside,0);
  outline: 2px solid darkred;
  transition: .4s;
}
*:focus-visible {
  outline: none;
  anchor-name: --focus;
}
```

Use Tab to navigate the demo below:

<p class="codepen" data-height="800" data-default-tab="result" data-slug-hash="ByjgRgM" data-pen-title="Universal focus (use tab to navigate)" data-preview="true" data-user="t_afif" style="height: 800px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/ByjgRgM">
  Universal focus (use tab to navigate)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>
