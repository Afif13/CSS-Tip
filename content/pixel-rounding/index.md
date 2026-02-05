---
layout: layouts/post.njk
title: No more pixel rounding issues!
description: One line of code to fix all your pixel rounding issues
date: 2024-05-25
tags: posts
---

One line of code that looks strange and confusing. You may think it's not even CSS but it will save you many times in the future:

```css
.container {
  width: calc-size(auto,round(down,size,1px)); 
  /* works with height as well */
}
```

It will make sure the width of your element is always an integer! No more decimal and rounding issues! 

The behavior of `width:auto` with an upgrade. 

⚠️ Limited support (Chrome-only for now) 

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="rNgLyJz" data-pen-title="width: auto with pixel rounding" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/rNgLyJz">
  width: auto with pixel rounding</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

If you are explicitly setting a size you can use the following which is widely supported:

```css
.container {
  width: round(down,X,1px);  /* instead of width: X */

  /* X can be anything (100%,10rem,50vw,45cqi, etc) */
}
```