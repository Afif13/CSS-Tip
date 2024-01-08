---
layout: layouts/post.njk
title: Border with inner radius for your images
description: Two lines of code to add an inner radius to your images
date: 2024-01-03
tags: posts
---

Add a border with an inner radius to your image using a simple code.
* No extra element
* No pseudo-element
* Only 2 CSS declarations


{% image "./image.png", "images with inner border radius" %}

```css
img {
  border-radius: 20%; /* works with any value or without */
  border-image: 
    conic-gradient(#A7DBD8 0 0) /* border color */
    fill 0//20px; /* border thickness */
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="abMvjZj" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/abMvjZj">
  Inner radius to image element</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

Another syntax

```css
img {
  border-radius: 20%; /* works with any value or without */
  border-image: conic-gradient(#A7DBD8 /* border color */ 0 0) fill 0;
  padding: 20px; /* border thickness */
}
```
