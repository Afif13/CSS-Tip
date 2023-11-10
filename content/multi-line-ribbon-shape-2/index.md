---
layout: layouts/post.njk
title: Responsive multi-line Ribbon Shape II
description: A few gradients trick to create a responsive ribbon shape
date: 2023-11-10
tags: posts
---

After [the previous one](/multi-line-ribbon-shape/), here is another concept of Responsive Ribbon Shape using the same code structure.
* Only one element
* Works with multi-line text
* Optimized with CSS variables and Math functions

{% image "./image.png", "CSS only ribbon shapes with multi-line text" %}

```css
.ribbon {
  --r: .5em;  /* control the cutout of the ribbon */
  --a: 20deg; /* control the angle of the folded part */
  --w: 5em;   /* control the width of the folded part  */
  --c: #d81a14;
  
  padding-inline: calc(1lh*tan(var(--a)/2) + .3em);
  margin-block: calc(var(--w)*sin(var(--a)));
  background-image: 
    linear-gradient(var(--c) 70%,#0000 0), 
    linear-gradient(to bottom left,#0000 50%, color-mix(in srgb,var(--c),#000 40%) 51% 84%,#0000 85%);
  background-position: 0 .15lh;
  background-size: 100% 1lh;
  position: relative;
  clip-path: polygon(
    0 .15lh,
    calc(100% - .7lh/sin(var(--a))) .15lh,
    calc(100% - .7lh/sin(var(--a)) - 999px) calc(.15lh - 999px*tan(var(--a))),
    100% -999px,
    100% .15lh,
    calc(100% - .7lh*tan(var(--a)/2)) .85lh,
    100% 1lh,
    100% calc(100% - .15lh),
    calc(.7lh/sin(var(--a))) calc(100% - .15lh),
    calc(.7lh/sin(var(--a)) + 999px) calc(100% - .15lh + 999px*tan(var(--a))),
    0 999px,
    0 calc(100% - .15lh),
    calc(.7lh*tan(var(--a)/2)) calc(100% - .85lh),
    0 calc(100% - 1lh)
   );
}
.ribbon:before,
.ribbon:after {
  content:"";
  position: absolute;
  height: .7lh;
  width: var(--w);
  background: color-mix(in srgb,var(--c),#000 40%);
  rotate: var(--a);
}
.ribbon:before {
  top: .15lh;
  right: 0;
  transform-origin: top right;
  clip-path: polygon(0 0,100% 0,calc(100% - .7lh/tan(var(--a))) 100%,0 100%, var(--r) 50%);
}
.ribbon:after {
  bottom: .15lh;
  left: 0;
  transform-origin: bottom left;
  clip-path: polygon(calc(.7lh/tan(var(--a))) 0,100% 0,calc(100% - var(--r)) 50%,100% 100%,0 100%);
}
```


<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="abXWomd" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/abXWomd">
  CSS-only Multi-line Responsive Ribbon</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

An interactive version to see how the shape fit its content. Edit the text and see the magic 

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="BaMRQor" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/BaMRQor">
  CSS-only Multi-line Responsive Ribbon (interactive)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More Ribbon Shapes: [css-generators.com/ribbon-shapes](https://css-generators.com/ribbon-shapes/)