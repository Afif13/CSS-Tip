---
layout: layouts/post.njk
title: Border-only breadcrumb shape using modern CSS
description: A few lines of code to create a border-only breadcrumb shape that you can easily adjust
date: 2024-12-05
tags: posts
---

Create a border-only [breadcrumb shape](https://css-shape.com/breadcrumb/) using a few lines of code and modern CSS.
* No extra element
* Powered by `clip-path` & math functions
* Optimized with CSS variables

{% image "./image.png", "Border-only breadcrumb shape using CSS" %}

```css
.breadcrumb {
  --b: 5px;    /* the border thickness */
  --a: 40deg;  /* control the shape */
  --c: #64908A;

  line-height: 1.8; /* control the height  */
  padding-inline: calc(.5lh*tan(var(--a)) + var(--b)/cos(var(--a)));
  position: relative;
}
.breadcrumb:before {
  content:"";
  position: absolute;
  inset: 0;
  background: var(--c);
  clip-path: polygon(0 0,calc(100% - .5lh*tan(var(--a))) 0,100% 50%,calc(100% - .5lh*tan(var(--a))) 100%,0 100%,calc(.5lh*tan(var(--a))) 50%,0 0,calc(var(--b)*(tan(var(--a)) + 1/cos(var(--a)))) var(--b), calc(.5lh*tan(var(--a)) + var(--b)/cos(var(--a))) 50%,calc(var(--b)*(tan(var(--a)) + 1/cos(var(--a)))) calc(100% - var(--b)),calc(100% - .5lh*tan(var(--a)) - var(--b)*(1/cos(var(--a)) - tan(var(--a)))) calc(100% - var(--b)),calc(100% - var(--b)/cos(var(--a))) 50%,calc(100% - .5lh*tan(var(--a)) - var(--b)*(1/cos(var(--a)) - tan(var(--a)))) var(--b),calc(var(--b)*(tan(var(--a)) + cos(var(--a)))) var(--b))
}
.breadcrumb:first-child:before {
  clip-path: polygon(0 0,calc(100% - .5lh*tan(var(--a))) 0,100% 50%,calc(100% - .5lh*tan(var(--a))) 100%,0 100%,0 0,var(--b) var(--b),var(--b) calc(100% - var(--b)),calc(100% - .5lh*tan(var(--a)) - var(--b)*(1/cos(var(--a)) - tan(var(--a)))) calc(100% - var(--b)),calc(100% - var(--b)/cos(var(--a))) 50%,calc(100% - .5lh*tan(var(--a)) - var(--b)*(1/cos(var(--a)) - tan(var(--a)))) var(--b),var(--b) var(--b)) 
}
.breadcrumb:last-child:before {
  clip-path: polygon(0 0,100% 0,100% 50%,100% 100%,0 100%,calc(.5lh*tan(var(--a))) 50%,0 0,calc(var(--b)*(tan(var(--a)) + 1/cos(var(--a)))) var(--b), calc(.5lh*tan(var(--a)) + var(--b)/cos(var(--a))) 50%,calc(var(--b)*(tan(var(--a)) + 1/cos(var(--a)))) calc(100% - var(--b)),calc(100% - var(--b)) calc(100% - var(--b)),calc(100% - var(--b)) var(--b),calc(var(--b)*(tan(var(--a)) + cos(var(--a)))) var(--b))
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="wBwMJaz" data-pen-title="Border-only breadcrumb shape" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/wBwMJaz">
  Border-only breadcrumb shape</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More CSS Shapes: [css-shape.com](https://css-shape.com/)