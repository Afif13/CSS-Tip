---
layout: layouts/post.njk
title: Float an element to the bottom corner
description: Use shape-outside to place an element on the bottom corner
date: 2022-06-22
tags: posts
---

Make an element float to the bottom corner of your text content
* Minimal HTML code
* No JavaScript
* No media query

{% image "./float.png", "An image float at the bottom corner of the text" %}

```html
<div class="wrapper">
  <p>
    <span class="float"><img src="" alt=""></span>
    ....
  </p>
</div>
```

```css
.wrapper {
  display: flex;
}
.float {
  float: right; 
  height: 100%; 
  margin-left: 15px;
  display: flex; 
  align-items: flex-end; 
  /* 100px = image height */
  shape-outside: inset(calc(100% - 100px) 0 0); /* (6) */
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="mdXZrEG" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/mdXZrEG">
  Float element to bottom corner</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [css-tricks.com/float-an-element-to-the-bottom-corner](https://css-tricks.com/float-an-element-to-the-bottom-corner/)