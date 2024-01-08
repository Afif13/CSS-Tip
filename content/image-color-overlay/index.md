---
layout: layouts/post.njk
title: A color overlay above your images
description: Use outline to add an overlay to your image
date: 2022-04-07
tags: posts
---

Add a color overlay above your image using only 3 declarations
* No extra element (only the `<img>` tag)
* No pseudo element
* Works with rounded image

You can also have a cool transition on hover

{% image "./overlay.png", "A color overlay above an image" %}

```css
img {
  outline: 100vmax solid rgb(0 0 0/var(--_o,50%));
  outline-offset: -100vmax;
  /* keep only the image area visible */
  mask: linear-gradient(#000 0 0); 
  
  transition: outline-color .4s;
}
img:hover {
  --_o: 0%;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="popLNXV" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/popLNXV">
  Overlay image (no extra element)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
