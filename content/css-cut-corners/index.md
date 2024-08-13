---
layout: layouts/post.njk
title: Cut the corners of your element
description: Use CSS mask to cut the four corners of an element with a circular shapes
date: 2022-09-08
tags: posts
---

How much code is needed to cut the four corners of an element? Also known as inverted `border-radius`
* One Property
* One Gradient

Use an online generator to easily get the code: [css-generators.com/custom-corners](https://css-generators.com/custom-corners/)

{% image "./cut-corners.png", "An element with 4 cut corners" %}

```css
.corner {
  --s: 60px; /* control the radius of the cut */
  mask: radial-gradient(var(--s) at var(--s) var(--s),#0000 98%,#000) calc(-1*var(--s)) calc(-1*var(--s));
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="xxjZJGW" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/xxjZJGW">
  CSS Only cut corners</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More detail: [css-tricks.com/cut-corners-using-css-mask-and-clip-path-properties](https://css-tricks.com/cut-corners-using-css-mask-and-clip-path-properties/)