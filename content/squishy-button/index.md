---
layout: layouts/post.njk
title: A Squishy Button with a Hover/Click Effect
description: Using the shape() function to add a fancy shape to a button element
date: 2026-03-12
tags: posts
---

Use the `shape()` function to create a fancy frame around a button element with a cool animation on hover and on click.

{% image "./image.png", "CSS-only squishy button" %}

```css
button {
  background: #c1121f;
  color: #fff;
  font-size: 50px;
  line-height: 1.8;
  transition: .3s ease-out;
  cursor: pointer;
}
button:hover {
  transition: 1s linear(/* from https://linear-easing-generator.netlify.app/ */);
}
button:active {
  transition: .25s;
}
button span {
  display: block;
  transition: inherit;
}
button:active span {
  scale: .85;
}
button {  
  /* Shape #1 */
  clip-path: shape(/* from https://css-generators.com/fancy-frame/ */); 
}
button:hover {
  /* Shape #2 */
  clip-path: shape(/* from https://css-generators.com/fancy-frame/ */);
}
button:active {
  /* Shape #3 */
  clip-path: shape(/* from https://css-generators.com/fancy-frame/ */);
}
```

<p class="codepen" data-height="400" data-pen-title="Squishy button using shape()" data-preview="true" data-default-tab="result" data-slug-hash="ZYpLGvX" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZYpLGvX">
  Squishy button using shape()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

You can use my online generator to the get `shape()` code: [css-generators.com/fancy-frame](https://css-generators.com/fancy-frame/).

First, identify the height of the element (in our case, it's `90px` (`1.8 x 50px`)). Then, take half of that value (`45px`). In the generator, fix the values of the granularities and the shape ID (keep the vertical granularity at the smallest value). Then, you generate the first shape by setting the size to `0` and the radius to `45`. For the second shape, increase the size slightly and decrease the radius by the same amount (e.g., `15` and `30`). Same thing for the third shape (e.g., `22` and `23`). 

The sum of the size and radius must always remain the same (`45px` in our case), and you should keep the same granularities. The shape ID can be different if you want another kind of animation.


{% image "./image1.png", "Overview of the frame generator" %}