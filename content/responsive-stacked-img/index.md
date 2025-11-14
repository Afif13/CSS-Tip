---
layout: layouts/post.njk
title: Responsive List of Stacked/Overlapping Images
description: A few lines of modern CSS to create a horizontal list of responsive stacked images
date: 2025-11-13
tags: posts
---

Using modern CSS and a few lines of code to create a responsive list of stacked images. The overlap between the images will adjust automatically based on the number of items and the available space. No hardcoded values, no magic numbers, and the gap is transparent!


{% image "./image.png", "CSS-only responsive stacked images" %}

```css
.container {
  --s: 120px; /* image size*/
  --g: 12px;  /* the gap */ 
  
  display: flex;
  container-type: inline-size;
}
.container img {
  width: var(--s);
  border-radius: 50%;
  --_m: min((100cqw - sibling-count()*var(--s))/(sibling-count() - 1),var(--g));
  margin-right: var(--_m);
  mask: radial-gradient(50% 50% at var(--_r,calc(150% + var(--_m))),
    #0000 calc(100% - 1px + var(--g)),#000 calc(100% + var(--g)));
}
.container.reverse img {
  --_r:calc(-50% - var(--_m));
}
.container img:last-child {
  margin: 0;
}
.container:not(.reverse) img:last-child,
.container.reverse img:first-child {
  mask: none;
}
```

Resize the demo below to see how the image behaves:

<p class="codepen" data-height="650" data-default-tab="result" data-slug-hash="azNvBJV" data-pen-title="Responsive Stacked/Overlapping images" data-preview="true" data-user="t_afif" style="height: 650px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/azNvBJV">
  Responsive Stacked/Overlapping images</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Another version with a hover effect to expand the images. Notice how the hover effect only works when there is an overlap.

<p class="codepen" data-height="650" data-default-tab="result" data-slug-hash="VYavBwN" data-pen-title="Responsive Stacked/Overlapping images with hover" data-preview="true" data-user="t_afif" style="height: 650px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/VYavBwN">
  Responsive Stacked/Overlapping images with hover</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>