---
layout: layouts/post.njk
title: A fancy hover effect using outline
description: Use outline to create a simple but nice hover effect
date: 2022-08-24
tags: posts
---

Add a cool hover effect to your images using a few lines of code
* No extra element (only the `<img>` tag)
* No pseudo element
* Using only the outline property
* Optimized with CSS variables


{% image "./hover-effect.png", "A fancy hover effect using CSS outline" %}

```css
img {
  --s: 250px;   /* the size of the image */
  --b: 8px;     /* the border thickness*/
  --g: 14px;    /* the gap */
  --c: #4ECDC4; /* the color */
  
  width: var(--s);
  aspect-ratio: 1;
  outline: calc(var(--s)/2) solid #0009;
  outline-offset: calc(var(--s)/-2);
  transition: 0.3s;
}
img:hover {
  outline: var(--b) solid var(--c);
  outline-offset: var(--g);
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="JjLVLPL" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/JjLVLPL">
  Frame hover effect with one element</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

