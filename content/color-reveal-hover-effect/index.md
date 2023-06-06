---
layout: layouts/post.njk
title: Color your image with a sliding hover effect
description: Reveal the color of a black & white image using a simple code
date: 2023-06-06
tags: posts
---

Reveal the colors of your images with a sliding animation on hover
* No extra element (only the `<img>` tag)
* No pseudo-element
* Less than 15 CSS declarations
* Easily control the sliding direction


{% image "./image.png", "CSS reveal hover effect" %}

```html
<!-- I have to duplicate the url, that's the only drawback -->
<img src="https://picsum.photos/id/56/250/250" style="--i:url(https://picsum.photos/id/56/250/250)" alt="">
```

```css
img {
  --s: 200px; /* the image size */
  
  width: var(--s);
  height: var(--s); /* better than aspect-ratio in case the image has a height attribute */
  box-sizing: border-box;
  background: var(--i) 50%/cover #000;
  background-blend-mode: luminosity;
  object-fit: cover;
  object-position: right;
  padding-left: var(--s);
  transition: .5s;
}
img:hover {
  padding: 0;
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="gOQYqRp" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/gOQYqRp">
  Color your image with a sliding hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


