---
layout: layouts/post.njk
title: Remove the unit from any CSS value
description: A hacky CSS trick to transform an length value into an integer
date: 2024-09-19
tags: posts
---

Do you want to convert a length value to a unitless value? 

It's possible to remove the unit from any CSS value to get an integer!

⚠️ A hacky experimentation to use with caution ⚠️

```css
@property --unitless-val {
  syntax: '<integer>';
  inherits: true;
  initial-value: 0; 
}
@property --_u {
  syntax: '<length>';
  inherits: true;
  initial-value: 0; 
}
:root {
  --val: 25em; /* use any length unit (px, em, ex, ch, rem, ...)*/
  
  /* we multiply then divide with the biggest value to get one unit */
  --_m: 3.35544e07; /* this value depend on the browser */
  --_u: calc(var(--val)*var(--_m));
  --unit: calc(var(--_u)/var(--_m)); /* = 1em  */
  
  --unitless-val: tan(atan2(var(--val),var(--unit))); /* = 25 */
  /* In the near future we can do
    --unitless-val: calc(var(--val)/var(--unit));
  */
}
/* we need a different value for firefox */
@supports (-moz-appearance: none) {
  :root {
    --_m: 3.40282e38;
  }
}
```
You may think we can use `infinity` as the biggest value but it won't work because dividing by infinity will always result in 0.

Tested on Firefox, Chrome and Edge. On Firefox, it works only with `px` because the value is converted to `px` inside the `--_u` variable.

<p class="codepen" data-height="400" data-default-tab="css,result" data-slug-hash="qBzePdX" data-pen-title="Remove the unit from any CSS value!" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/qBzePdX">
  Remove the unit from any CSS value!</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>