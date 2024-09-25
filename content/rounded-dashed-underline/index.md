---
layout: layouts/post.njk
title: "A rounded & dashed underline"
description: A combination of gradients to create a rounded dashed underline
date: 2022-02-01
tags: posts
---

Add a nice rounded dashed underline to your text.
* No SVG, No image
* No extra element
* No pseudo-element
* Works with multi-lines of text
* Easy to update using CSS variables

{% image "./dash.png", "A text with a rounded dashed underline" %}

```css
p span {
  --w: 20px;    /* the width of dashes */
  --h: 5px;     /* the height of dashes */
  --c: #4b9ed9; /* the color */
  
  line-height: calc(1.2em + 2*var(--h));
  padding-bottom: calc(2*var(--h));
  background: bottom/calc(2*var(--w)) calc(2*var(--h)) space no-repeat;
  --_g: calc(var(--w)/2) top 50%,var(--c) 90%,#0000 105%;
  background-image: 
   radial-gradient(var(--h) at left  var(--_g)),   
   radial-gradient(var(--h) at right var(--_g)),   
   linear-gradient(90deg,#0000 calc(var(--w)/2),var(--c) 0 calc(3*var(--w)/2), #0000 0);
  -webkit-box-decoration-break: clone;
          box-decoration-break: clone;
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="dyZGBvN" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dyZGBvN">
  Multi-line rounded dashes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>