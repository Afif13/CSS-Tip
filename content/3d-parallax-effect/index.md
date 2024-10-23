---
layout: layouts/post.njk
title: 3D parallax effect on hover
description: A perfect 3D parallax illusion using a single image element
date: 2024-10-23
tags: posts
---

After [the previous effect](/3d-parallax-image/), I am trying another concept of 3D parallax effect with a better illusion!
* No extra element (only the `<img>` tag)
* No pseudo-element
* Less than 15 CSS declarations


{% image "./image.png", "A 3D parallax effect on images" %}

```css
img {
  --s: 300px; /* the image size */
  
  width: var(--s);
  aspect-ratio: 1;
  box-sizing: border-box;
  padding-inline: calc(var(--s)/10) 0;
  object-fit: cover;
  border-radius: 20px;
  transform: perspective(350px) rotateY(calc(var(--_i,1)*10deg));
  transition: .5s;
}
img:hover {
  --_i: -1;
  padding-inline: 0 calc(var(--s)/10);
}
```

I am actually using 2 different images but only one image element is used in the code.

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="KKOXrer" data-pen-title="3D parallax effect on hover" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/KKOXrer">
  3D parallax effect on hover</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>