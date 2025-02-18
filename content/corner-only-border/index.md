---
layout: layouts/post.njk
title: Corner-only border around an image
description: Use CSS gradient and mask to create a Corner-only border around your image
date: 2021-11-03
tags: posts
---

Create a corner-only border around an image (or any element) using a few lines of code.

* No extra element
* No Pseudo-element
* Only three properties

{% image "./image.png", "image with corner-only border" %}


```css
img {
  --s: 80px; /* corner size */
  padding: 15px; /* the gap */
  border: 8px solid #69D2E7;
  mask:
    conic-gradient(at var(--s) var(--s),#0000 75%,#000 0)
     0 0/calc(100% - var(--s)) calc(100% - var(--s)),
    conic-gradient(#000 0 0) content-box;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="EaxVzyb" data-pen-title="Corner-only borders" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/EaxVzyb">
  Corner-only borders</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Another idea: [Corner-only borders with hover effect](/corner-only-border-image/)