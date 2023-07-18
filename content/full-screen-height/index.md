---
layout: layouts/post.njk
title: Full screen height container
description: Make your container fill all the screen height
date: 2021-12-15
tags: posts
---

Make your container fill all the screen height
* No cascading `height:100%`
* No side effects of the `100vh`
* Works with the default margin of `<body>`
* No overflow issue. The height will grow to fit the content.

```css
html {
  display: grid;
  min-height: 100%;
}
.box {
  height: 100%;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="oNGZjvL" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/oNGZjvL">
  Full height element</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More detail: [verpex.com/blog/website-tips/modern-layouts-using-css-grid](https://verpex.com/blog/website-tips/modern-layouts-using-css-grid)