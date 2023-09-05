---
layout: layouts/post.njk
title: Infinite shadow for your images
description: a small code to create an infinite shadow in any direction
date: 2023-09-05
tags: posts
---

Add an infinite shadow to your image in any direction using a few lines of code
* No extra element (only the `<img>` tag)
* No pseudo-elements
* Only 2 CSS properties
* Works with rounded corners


{% image "./image.png", "four images with an infinite shadow" %}

```css
img {
  --c: #A7DBD8;
  --s: 10px; /* the border thickness*/
  
  border-radius: 50%; /* optional */
  outline: var(--s) solid var(--c)
}
.top {
  border-image: 
   linear-gradient(var(--c) 50%,#0000 0) 
   fill 0//100vh var(--s);
}
.bottom {
  border-image: 
   linear-gradient(#0000 50%,var(--c) 0) 
   fill 0//100vh var(--s);
}
.right {
  border-image: 
   linear-gradient(90deg,#0000 50%,var(--c) 0) 
   fill 0//var(--s) 100vw;
}
.left {
  border-image: 
   linear-gradient(90deg,var(--c) 50%,#0000 0) 
   fill 0//var(--s) 100vw;
}
```

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="XWoNdGK" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWoNdGK">
  Infinite image shadow</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

