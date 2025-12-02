---
layout: layouts/post.njk
title: Gallery of Skewed Images with Hover Effect
description: Using modern CSS and corner-shape to add a fancy galley of images with a reveal hover effect
date: 2025-12-02
tags: posts
---

Another classic component made easy with modern CSS and the new `corner-shape`. A gallery of skewed images with a reveal effect on hover using a few lines of code. The skewing adjusts accordingly to the direction of the text. Another direction-aware shape!

{% image "./image.png", "CSS-only gallery of skewed images" %}


```css
.gallery {
  --s: 50px; /* control the skewing */
  
  display: flex;
  gap: 10px;
}
.gallery > img {
  flex: 1;
  border-start-start-radius: var(--s) 100%;
  border-end-end-radius: var(--s) 100%;
  margin-inline-end: calc(-1*var(--s));
  corner-shape: bevel;
  transition: .3s linear;
}
.gallery > img:hover {
  flex: 1.6;
}
.gallery > img:is(:first-child,:hover),
.gallery > img:hover + * {
  border-start-start-radius: 0 100%;
}
.gallery > img:is(:last-child,:hover),
.gallery > img:has(+ :hover) {
  border-end-end-radius: 0 100%;
  margin-inline-end: 0;
}
```

<p class="codepen" data-height="700" data-default-tab="result" data-slug-hash="NPNBVYq" data-pen-title="Gallery of skewed images (with hover effect)" data-preview="true" data-user="t_afif" style="height: 700px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/NPNBVYq">
  Gallery of skewed images (with hover effect)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Another implementation using `clip-path` with better, support but not direction-aware.

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="XJdBwxz" data-pen-title="Gallery of skewed images (with hover effect) II" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/XJdBwxz">
  Gallery of skewed images (with hover effect) II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
 <script async src="https://public.codepenassets.com/embed/index.js"></script>
