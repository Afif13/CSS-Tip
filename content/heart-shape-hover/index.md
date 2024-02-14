---
layout: layouts/post.njk
title: Heart shape with a sliding hover effect
description: A lovely animation to your heart shape image
date: 2024-02-14
tags: posts
---

Turn your image into a heart shape with a lovely hover animation 😍
* No extra element (only the `<img>` tag)
* No pseudo-elements
* Less than 15 CSS declarations

{% image "./image.png", "A CSS only heart shape for images" %}

```css
img {
  --s: 300px; /* image size */
  
  width: var(--s);
  padding: calc(var(--s)/2);
  box-sizing: border-box;
  background: #e5414e; /* heart color */
  aspect-ratio: 1;
  object-fit: cover;
  mask-border: radial-gradient(#000 69%,#0000 70%) 84.5%/50%;
  clip-path: polygon(-41% 0,50% 91%, 141% 0);
  transition: .6s padding-block, padding-inline 0s .6s;
}
img:hover {
  padding: 0;
  transition: .6s padding-inline, padding-block 0s;
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="abMPBdg" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/abMPBdg">
  Heart shape image reveal  ❤️</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


Related Article: [verpex.com/blog/website-tips/css-shapes-the-heart](https://verpex.com/blog/website-tips/css-shapes-the-heart)