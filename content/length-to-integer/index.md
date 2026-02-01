---
layout: layouts/post.njk
title: Remove the unit from any CSS value
description: A simple CSS trick to transform a length value into an number without its unit
date: 2024-09-19
tags: posts
---

Do you want to convert a length value to a unitless value?  It's possible with a simple CSS trick.


```css
/* register the value as a length */
@property --val {
  syntax: '<length>';
  inherits: true;
  initial-value: 0; 
}

:root {
  --val: 25em; /* use any length unit (px, em, ex, ch, rem, ...)*/
  
  /* divide it by 1px and you get a uniteless value */
  --unitless-val: calc(var(--val)/1px); 
  /* for better support you can do the below    
    --unitless-val: tan(atan2(var(--val),1px));
  */
}
/* As a bonus, you can also show the unitless value */
body:before {
  content: counter(c);
  counter-reset: c var(--unitless-val);
}
```

<p class="codepen" data-height="400" data-default-tab="css,result" data-slug-hash="qBzePdX" data-pen-title="Remove the unit from any CSS value!" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/qBzePdX">
  Remove the unit from any CSS value!</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

The same trick works with other type as well. Example with `angle`:

```css
/* register the value as an angle */
@property --val {
  syntax: '<angle>';
  inherits: true;
  initial-value: 0; 
}

:root {
  --val: 90deg; 
  --unitless-val: calc(var(--val)/1deg); 
  /* for better support you can do the below    
    --unitless-val: tan(atan2(var(--val),1deg));
  */
}
```