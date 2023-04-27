---
layout: layouts/post.njk
title: A reveal hover effect with a single element
description: Add a reveal animation to your image with a minimal code
date: 2023-04-27
tags: posts
---

Add a simple reveal animation to your images using a few lines of code
* No extra element (only the `<img>` tag)
* No pseudo-element
* Less than 10 CSS declarations
* Powered by `object-fit` and `object-position`
* Easily control the reveal direction

```css
img {
  --s: 200px; /* the image size */
  
  width: var(--s);
  height: var(--s); 
  box-sizing: border-box;
  object-fit: cover;
  cursor: pointer;
  transition: .5s;
}
img.left {
  object-position: right;
  padding-left: var(--s);
  background: #542437; /* the overlay color */
}
/* similar code for the other directions */

img:hover {
  padding: 0;
}
```


<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="GRYEZrr" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/GRYEZrr">
  A reveal hover effect with one element</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


