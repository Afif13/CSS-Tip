---
layout: layouts/post.njk
title: Corner-only border around an image
description: Use CSS gradient to create a Corner-only border around your image
date: 2021-11-03
tags: posts
---

Create a corner-only border around any element.

* No extra element
* No Pseudo-element
* Only background properties

You can also animate it on hover!

{% image "./image.png", "image with corner-only border" %}


```css
img {
  --b: 5px; /* border thickness */
  --c: #0000 25%,darkblue 0; /* define the color here */
  padding: 10px;
  background:
    conic-gradient(from 90deg  at top    var(--b) left  var(--b),var(--c)) 0    0,
    conic-gradient(from 180deg at top    var(--b) right var(--b),var(--c)) 100% 0,
    conic-gradient(from 0deg   at bottom var(--b) left  var(--b),var(--c)) 0    100%,
    conic-gradient(from -90deg at bottom var(--b) right var(--b),var(--c)) 100% 100%;
  background-size: 50px 50px; /* adjust border length here */
  background-repeat: no-repeat;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="abyEmgj" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/abyEmgj">
  Corner only frames</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [css-tricks.com/fancy-image-decorations-single-element-magic](https://css-tricks.com/fancy-image-decorations-single-element-magic/)

Another idea: [Corner-only borders with hover effect](/corner-only-border-image/)