---
layout: layouts/post.njk
title: Sliding reveal animation for your image
description: A cool reveal effect on hover with a sliding animation
date: 2023-06-10
tags: posts
---

Add a reveal effect to your image with a sliding animation on hover
* No extra element (only the `<img>` tag)
* No pseudo element
* Less than 10 CSS declarations


{% image "./image.png", "Sliding reveal animation" %}

```css
img {
  --s: 200px; /* the size of the image */
  
  width: var(--s);
  aspect-ratio: 1;
  box-sizing: border-box;
  object-fit: cover; 
  /* 8px = thickness  13px = gap (5px) + thickness (8px) */
  border-image: linear-gradient(#53777A 0 0) 1/8px/13px;
  object-position: top;
  padding-top: calc(2*var(--s)/3);
  transition: .5s;
}
img:hover {
  padding: 0;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="dyQPgWj" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dyQPgWj">
  Sliding reveal hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


