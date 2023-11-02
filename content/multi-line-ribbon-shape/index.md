---
layout: layouts/post.njk
title: Responsive multi-line Ribbon Shape
description: A few gradients trick to create a responsive ribbon shape
date: 2023-11-02
tags: posts
---

Place your text inside a responsive ribbon shape using a few lines of code.
* Only one element
* No pseudo-elements
* Works with multi-line text

{% image "./image.png", "CSS only ribbon shapes with multi-line text" %}

```css
.ribbon {
  --r: .5em;  /* control the cutout of the ribbon */
  --c: #d81a14;
  
  padding-inline: calc(.5em + var(--r));
  background-image: 
    linear-gradient(var(--c) 70%,#0000 0), 
    linear-gradient(to bottom left,#0000 50%, color-mix(in srgb,var(--c),#000 40%) 51% 84%,#0000 85%);
  background-position: 0 .15lh;
  background-size: 100% 1lh;
  clip-path: polygon(0 .15lh,100% .15lh,calc(100% - var(--r)) .5lh,100% .85lh,100% calc(100% - .15lh),0 calc(100% - .15lh),var(--r) calc(100% - .5lh),0 calc(100% - .85lh));
}
```


<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="XWOKEmG" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWOKEmG">
  CSS-only Multi-line Responsive Ribbon</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Here is an interactive demo where you can update the text content and see how the shape reacts

<p class="codepen" data-height="350" data-default-tab="result" data-slug-hash="ZEwOZVB" data-preview="true" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZEwOZVB">
  CSS-only Multi-line Responsive Ribbon (interactive)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More Ribbon Shapes: [css-generators.com/ribbon-shapes](https://css-generators.com/ribbon-shapes/)