---
layout: layouts/post.njk
title: A CSS-only custom cursor
description: Combine CSS and SVG to create any kind of fancy cursor
date: 2022-06-14
tags: posts
---

Create a custom cursor using CSS without external resources. Style your cursor like you do with a simple `<div>`!

Powered by CSS-in-SVG-in-CSS


```css
html {
/*
  - adjust the width,height and viewbox to control the size 
  - minify your CSS 
  - change all the # to %23
*/
  cursor: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 48 48"><foreignObject width="100%" height="100%"><div xmlns="http://www.w3.org/1999/xhtml" class="c"></div>%3Cstyle%3E.c{ ADD YOUR CSS HERE }%3C/style%3E</foreignObject></svg>')  
  24 24 /* control the offset */ , 
  auto; /* the fallback cursor */
}

```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="rNJPaJP" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/rNJPaJP">
  CSS only Custom cursor</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [verpex.com/blog/website-tips/creating-a-custom-cursor-using-css](https://verpex.com/blog/website-tips/creating-a-custom-cursor-using-css)