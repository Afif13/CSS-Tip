---
layout: layouts/post.njk
title: CSS Shapes using corner-shape
description: Recreate all the common CSS shapes using corner-shape and border-radius
date: 2025-09-24
tags: posts
---

Ready for [the new `corner-shape` property](https://frontendmasters.com/blog/drawing-css-shapes-using-corner-shape/)? It allows you to manipulate the shape of the corners, and by simply adjusting the `border-radius`, you can create most of the common CSS shapes. 

You can easily add borders to some shapes as well!

{% image "./image.png", "CSS-only shapes (triangle, rhombus, hexagon, etc.)" %}

⚠️ Limited support (Chrome-only for now) ⚠️

## Triangles

Isosceles triangles

```css
.triangle {
  corner-shape: bevel;
  aspect-ratio: 1/cos(30deg);
  border-radius: 50%/100% 100% 0 0; /* OR 50%/0 0 100% 100% */
}
``` 

```css
.triangle {
  corner-shape: bevel;
  aspect-ratio: cos(30deg);
  border-radius: 0 100% 100% 0/50%; /* OR 100% 0 0 100%/50% */
}
``` 

Right triangles

```css
.triangle {
  corner-shape: bevel;
  border-[top|bottom]-[right|left]-radius: 100%;
}
``` 

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="yyNjmLw" data-pen-title="Triangle shapes using corner-shape" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yyNjmLw">
  Triangle shapes using corner-shape</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## Rhombus

```css
.rhombus {
  border-radius: 50%;
  corner-shape: bevel;
  aspect-ratio: 1;
} 
```

## Octagon

```css
.octagon {
  border-radius: calc(100%/(2 + sqrt(2)));
  corner-shape: bevel;
  aspect-ratio: 1;
}
``` 

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="PwqevXP" data-pen-title="Adding border to octagon and rhombus" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/PwqevXP">
  Adding border to octagon and rhombus</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## Hexagon

```css
.hexagon {
  border-radius: 50% / 25%; /* OR 25% / 50% */
  corner-shape: bevel;
  aspect-ratio: cos(30deg); /* OR 1/cos(30deg) */
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="yyNjgzR" data-pen-title="Hexagon shapes (with border!)" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yyNjgzR">
  Hexagon shapes (with border!)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## Trapezoid & Parallelogram

```css
.trapezoid {
  border-radius: 80px / 100% 0 100% 0;
  corner-shape: bevel;
}
.parallelogram {
  border-radius: 80px / 100% 100% 0 0;
  corner-shape: bevel;
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="WbvJVdW" data-pen-title="Trapezoid &amp;amp; Parallelogram" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/WbvJVdW">
  Trapezoid &amp; Parallelogram</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


## Arrow

```css
.arrow {
  corner-shape: notch bevel bevel notch;
  border-radius: 60% 40% 40% 60%/25% 50% 50% 25%;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="WbvyNMM" data-pen-title="Arrow shape" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/WbvyNMM">
  Arrow shape</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## Cube & 3D box

```css
.cube {
  --d: 30px; /* control the depth */
  
  border-radius: 0 var(--d);
  corner-shape: bevel;
  border-right:  var(--d) solid #0004;
  border-bottom: var(--d) solid #0008;
  background: #9CC4E4; 
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="EaPVaMB" data-pen-title="3D box using corner-shape" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/EaPVaMB">
  3D box using corner-shape</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

More CSS Shapes: [css-shape.com](https://css-shape.com/)

