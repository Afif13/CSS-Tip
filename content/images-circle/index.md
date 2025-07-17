---
layout: layouts/post.njk
title: How to place images around a circle
description: A simple CSS code to correctly place a set of images (or any elements) around a circle
date: 2025-07-17
tags: posts
---

Using `offset` combined with [the new `sibling-index()` and `sibling-count()` functions](/element-index/), we can easily and precisely place images (or any elements) around a circle using a few lines of code.

{% image "./image.png", "CSS-only images around a circle" %}


```css
.container {
  display: inline-grid;
}
.container img {
  --s: 150px; /* image size */
  --g: 10px;  /* control the gap */
  
  width: var(--s);
  grid-area: 1/1;
  offset: 
    circle(calc(var(--s)/(2*sin(.5turn/sibling-count())) + var(--g))) 
    calc(100%*sibling-index()/sibling-count()) 0deg;
}
```


Add/remove images in the demo below, and see how they are perfectly placed regardless of their number.


<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="jEbbLZb" data-pen-title="Images around a circle" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/jEbbLZb">
  Images around a circle</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

If you don't want to be precise, you can simplify the code like below

```css
.container {
  display: inline-grid;
}
.container img {
  width: 150px;
  grid-area: 1/1;
  /* adjust the 180px to control the placement */
  offset: circle(180px) calc(100%*sibling-index()/sibling-count()) 0deg;
}
```

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="myeeMMQ" data-pen-title="Images around a circle" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/myeeMMQ">
  Images around a circle</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


We go fancy by adding a nice entry animation using `@starting-style`

```css
.container img {
  transition: 1s 1s;
  @starting-style {
    offset: circle(0px) 0% 0deg;
  }
}
```

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="wBKKqjw" data-pen-title="Images around a circle + animations" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/wBKKqjw">
  Images around a circle + animations</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>