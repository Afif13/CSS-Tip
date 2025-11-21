---
layout: layouts/post.njk
title: Responsive Circular List of Stacked/Overlapping Images
description: Images placed around a circle with a slight overlap and a nice hover effect
date: 2025-11-18
tags: posts
---

Building on the idea from [the previous post](/responsive-stacked-img/), I created a circular list instead of a horizontal one. The position of the images will adjust according to the container size and available space. You also have a cool hover effect that reveals the images, and the gap between them is transparent!


{% image "./image.png", "CSS-only circular list of stacked images" %}

```css
.container {
  --s: 120px; /* image size */
  --g: 14px;  /* the gap */ 
  
  display: grid;
  place-content: center;
  aspect-ratio: 1;
  container-type: inline-size;
}
.container img {
  grid-area: 1/1;
  width: var(--s);
  border-radius: 50%;
  cursor: pointer;
  --_r: min(50cqw - var(--s)/2,(var(--s) + var(--g))/(2*sin(.5turn/sibling-count())));
  --_i: calc(1turn*sibling-index()/sibling-count() + var(--_ii,0deg));
  --_j: calc(1turn*(sibling-index() + 1)/sibling-count() + var(--_jj,0deg));
  --_a: calc(2*asin((var(--s) + var(--g))/(2*var(--_r))) - 1turn/sibling-count());
  transform: rotate(calc(-1*var(--_i))) translate(var(--_r)) rotate(var(--_i));
  mask: radial-gradient(50% 50% at 
    calc(50% + var(--_r)*(cos(var(--_j)) - cos(var(--_i))))
    calc(50% + var(--_r)*(sin(var(--_i)) - sin(var(--_j)))),
     #0000 calc(100% - 1px + var(--g)),#000 calc(100% + var(--g)));
  transition: --_i .3s linear,--_j .3s linear;
}
.container.reverse img {
  --_i: calc(1turn*sibling-index()/sibling-count() - var(--_ii,0deg));
  --_j: calc(1turn*(sibling-index() - 1)/sibling-count() - var(--_jj,0deg));
}
.container:has(:hover) img {
  --_ii: var(--_a);
  --_jj: var(--_a);
}
.container img:hover {
  --_ii: 0deg;
    z-index: 1;
}
.container:not(.reverse) img:has(+ :hover),
.container.reverse img:hover + *,
.container:not(.reverse):has(:first-child:hover) img:last-child,
.container.reverse:has(:last-child:hover) img:first-child {
  --_jj: 0deg;
}
```

Resize the demo below to see how the image behaves. If there is sufficient space, the images will be placed as close as possible without overlap.

<p class="codepen" data-height="700" data-default-tab="result" data-slug-hash="MYyobpb" data-pen-title="Responsive Circular List of images with hover effect" data-preview="true" data-user="t_afif" style="height: 700px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/MYyobpb">
  Responsive Circular List of images with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>