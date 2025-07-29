---
layout: layouts/post.njk
title: Responsive infinite logo marquee
description: Use modern CSS and a few lines of code to create an infinite scroll animation 
date: 2025-07-29
tags: posts
---

With [the powerful shape() function](https://css-tricks.com/better-css-shapes-using-shape-part-1-lines-and-arcs/) and the new [sibling-index()/sibling-count() functions](/element-index/), we can create an infinite logo marquee using a few lines of code. 

* Responsive (It doesn't depend on the container width) 
* Works with any number of images
* Easy to control using CSS variables
* No magic numbers


{% image "./image.png", "A CSS-only arrow-like rectangle" %}

```html
<div class="container">
  <img src="">
  <img src="">
  <!-- as many images as you want -->
</div>
```

```css
.container {
  --s: 150px; /* size of the logos */
  --d: 8s; /* animation duration */
  --n: 4; /* number of visible logos */
  
  display: flex;
  overflow: hidden;
}
img {
  width: var(--s);
  offset: shape(from calc(var(--s)/-2) 50%,hline by calc(sibling-count()*max(100%/var(--n),var(--s))));
  animation: x var(--d) linear infinite calc(-1*sibling-index()*var(--d)/sibling-count());
}
@keyframes x { 
  to {offset-distance: 100%}
}
```

⚠️ Limited support (Chrome only for now) ⚠️

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="QwjGqEJ" data-pen-title="Responsive infinite logo marquee" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/QwjGqEJ">
  Responsive infinite logo marquee</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

The technique is not limited to image elements. It works with any kind of content. 

The only requirement is to have equal-width items:

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="vENyead" data-pen-title="Infinite scroll animation" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/vENyead">
  Infinite scroll animation</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

<br>

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="vENyewr" data-pen-title="Responsive Infinite marquee animation" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/vENyewr">
  Responsive Infinite marquee animation</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>