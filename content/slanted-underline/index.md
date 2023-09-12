---
layout: layouts/post.njk
title: Slanted underline with hover effect
description: A simple code to add a slanted underline to your text
date: 2023-09-12
tags: posts
---

Add a slanted underline to your text with a nice hover effect using a simple code
* Minimal HTML
* No pseudo-elements
* Works with multi-line text
* Optimized with CSS variables


{% image "./image.png", "text with slanted underline" %}

```html
<h2><span>Gingerbread jelly beans</span></h2>

```

```css
h2 {
  --a: -45deg; /* control the angle */
  --t: .23em; /* thickness of the underline */ 
  color: #F1D4AF;
}

h2 span {
  --_s: calc(var(--t)*cos(var(--a)));
  background:
    linear-gradient(var(--a),#0000 var(--_s),currentColor 0 calc(100% - var(--_s)),#0000 0) 
    bottom/var(--i,90%) var(--t) no-repeat;
  padding: 0 .25em calc(var(--t) + .1em);
  -webkit-box-decoration-break: clone;
          box-decoration-break: clone;
  transition: .3s;
}
h2:hover span {
  --i: 100%;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="MWZmGRo" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/MWZmGRo">
  CSS-only Slanted underline</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>