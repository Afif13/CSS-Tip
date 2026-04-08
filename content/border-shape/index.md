---
layout: layouts/post.njk
title: Let's Reshape the Web using border-shape!
description: A new property to easily create CSS shapes while preserving borders, shadows, outlines, etc
date: 2026-04-08
tags: posts
---

To create [CSS Shapes](https://css-shape.com/), I mainly rely on clipping (using `clip-path`) or masking (using `mask`). Both are very powerful and can be used to create all the possible shapes. However, they are limited if we want to add decorations such as borders and shadows. 

The `corner-shape` property is a good alternative that allows us to [create CSS shapes with decorations](/corner-shape/). However, since it's only about shaping the corners, it remains limited to a subset of shapes.

Another alternative is the new and powerful `border-shape`.

{% image "./image.png", "Showing the difference between clip-path and border-shape" %}

`border-shape` doesn't perform clipping or masking; it "shapes" the whole element, including its decorations (borders, shadows, and outlines). And guess what? It takes the same values as `clip-path`  (`polygon()`, `shape()`, `inset()`, `circle()`, etc.). You don't have to learn something new, use `border-shape` instead of `clip-path` and see the magic in action!


```css
.shape {
  /* Old code */
  clip-path: shape() | polygon() | circle() | ...;
  /* New code */
  border-shape: shape() | polygon() | circle() | ...;
}

```

It's Chrome-only for now (starting from V147)

<p class="codepen" data-height="400" data-pen-title="Clip-path vs border-shape" data-preview="true" data-default-tab="result" data-slug-hash="pvEZBmQ" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/pvEZBmQ">
  Say hello to border-shape</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

### Will clip-path and mask become obsolete?

Not really. `mask` is useful for shapes that have a repeating pattern since it relies on gradients, and `clip-path` is useful when you want to clip/hide part of an element or create reveal effects. Consider `border-shape` if you want to create static shapes with decorations. Otherwise, you can keep using the old methods.

Here are a few examples of shapes taken from my [CSS Shapes collection](https://css-shape.com/), where I am simply replacing `clip-path` with `border-shape`

{% image "./image1.png", "CSS-only shapes using border-shape" %}

<p class="codepen" data-height="650" data-pen-title="Shapes with border-shape" data-preview="true" data-default-tab="result" data-slug-hash="jEMvwyP" data-user="t_afif" style="height: 650px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/jEMvwyP">
  Shapes with border-shape</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Some of my generators are also updated to provide a border-only version using `border-shape`. 

* [Blob Shapes](https://css-generators.com/blob/)
* [Wavy Divider](https://css-generators.com/wavy-divider/)
* [Fancy Frames](https://css-generators.com/fancy-frame/)

{% image "./image2.png", "border-only shapes using border-shape" %}

That's all for now, but stay tuned for more advanced usage and fancy demos with `border-shape`!