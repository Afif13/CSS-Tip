---
layout: layouts/post.njk
title: Safe align your content
description: Learn about the keyword "safe" and how to use it
date: 2025-06-10
tags: posts
---

Do you know the `safe` keyword? In some specific cases, your content may overflow the container and you won't be able to scroll to it. It happens with some alignment configurations such as `center` and `end`.

`safe` can prevent this behavior! 


```css
/* default behavior, not always good 🤨 */
.box {
  justify-content: center; 
}

/* safe alignment! 😌 */
.box {
  justify-content: safe center; 
}
```

Resize the container below and toggle the safe option to see the difference.

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="EajoLOe" data-pen-title="Safe alignment" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/EajoLOe">
  Safe alignment</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


It works with all the alignment properties.

```css
.container {
  /* place-content, justify-content,  align-content */
  /* place-items, justify-items, align-items */
}
.element {
  /* place-self, justify-self, align-self: */
}
```

It's not only limited to flexbox and CSS Grid, it's also applicable to block layout:

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="QwbaBQX" data-pen-title="Safe alignment with block containers" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/QwbaBQX">
  Safe alignment with block containers</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


Note that `auto` margin is another alternative for safe alignment:

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="ByNJvJN" data-pen-title="Safe alignment with auto margin" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ByNJvJN">
  Safe alignment with auto margin</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

 