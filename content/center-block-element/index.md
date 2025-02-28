---
layout: layouts/post.njk
title: A new way to center block elements using place-self
description: A modern way to center block elements using place-self instead of auto margin and max-width
date: 2024-12-06
tags: posts
---

A new way to center block elements is available! One line of code and you can replace the use of `margin: auto` combined with `width`/`max-width`.

```css
.box {
  place-self: center; /* OR justify-self: center */
}
```

The support is still not good. Use the latest version of Chrome to test:

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="ByBKNPP" data-pen-title="justify-self on block element" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ByBKNPP">
  justify-self on block element</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Using `place-items: center` on a parent element will do the same. It's useful if you want to center all the elements inside a container.

```css
.container {
  place-items: center; /* OR justify-items: center */
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="wBwGKaN" data-pen-title="justify-items on block elements" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/wBwGKaN">
  justify-items on block elements</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
