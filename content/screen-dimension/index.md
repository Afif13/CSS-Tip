---
layout: layouts/post.njk
title: Get the screen width & height without JavaScript
description: A few lines of CSS to get the screen width/height as integer values
date: 2024-07-16
tags: posts
---

Get the screen width and height as pixel values using a few lines of CSS.
* Powered by `@property` & trigonometric functions
* Unitless values so you can easily use them inside any formula
* Updates on screen resize (No need for JavaScript)


```css
@property --_w {
  syntax: '<length>';
  inherits: true;
  initial-value: 100vw; 
}
@property --_h {
  syntax: '<length>';
  inherits: true;
  initial-value: 100vh; 
}
:root {
  --w: tan(atan2(var(--_w),1px)); /* screen width */
  --h: tan(atan2(var(--_h),1px)); /* screen height*/
  /* The result is an integer without unit  */
}
```

Resize the below demo to see how the values update in real-time:

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="ExBVLBW" data-pen-title="Screen width/Screen height (CSS-only)" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ExBVLBW">
  Screen width/Screen height (CSS-only)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>