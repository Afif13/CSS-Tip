---
layout: layouts/post.njk
title: Hamburger menu icon
description: Use CSS gradients to create a menu icon
date: 2021-12-07
tags: posts
---

Create a CSS-only hamburger menu icon with 2 gradients. Adjust one value to control the size.

{% image "./menu.png", "A CSS-only menu icon" %}


```css
.menu {
  width:80px; /* update this to control the size */
  aspect-ratio:1;
  background:
    radial-gradient(closest-side at 50% 25%,#000 96%,#0000) top/20% 40%,
    linear-gradient(#000 50%,#0000 0) top/80% 40% repeat-y;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="zYEqGgR" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zYEqGgR">
  Hamburger menu</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [verpex.com/blog/website-tips/how-to-create-a-responsive-sidebar-menu-using-css](https://verpex.com/blog/website-tips/how-to-create-a-responsive-sidebar-menu-using-css)