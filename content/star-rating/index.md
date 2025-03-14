---
layout: layouts/post.njk
title: A single-element star rating component (without JS)
description: Using a few lines of code to transfom the native range slider into a star rating component
date: 2025-01-24
tags: posts
---

Transform the native range slider into a star rating component using a few lines of CSS and zero JavaScript. You can adjust the number of stars by simply changing the `max` attribute. 

Yes, you can click to update the rating. It's an interactive widget!

{% image "./image.png", "CSS-only star rating component" %}

```html
<input type="range" min="1" max="5">
```

```css
input[type="range"] {
  --s: 100px; /* control the size */
  
  height: var(--s);
  aspect-ratio: attr(max type(<integer>));
  padding-inline: calc(var(--s)/2);
  box-sizing: border-box;
  mask: url("data:image/svg+xml;utf8,<svg><path d='path_of_a_star_shape'/></svg>") 0/var(--s);
  appearance: none;
}
input[type="range"]::-webkit-slider-thumb{
  width: 1px;
  border-image: 
    conic-gradient(at calc(50% + var(--s)/2),#7b7b7b 50%,#fff220 0)
    fill 0//var(--s) calc(20*var(--s));
  appearance: none;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="GgKYbee" data-pen-title="CSS-Only  Rating Component (Click to update!)" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/GgKYbee">
  CSS-Only  Rating Component (Click to update!)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

We can update the code slightly to get a variation that works with half stars.

```html
<input type="range" min=".5" step=".5" max="5">
```

```css
input[type="range"] {
  --s: 100px; /* control the size*/
  
  height: var(--s);
  aspect-ratio: attr(max type(<integer>));
  padding-inline: calc(var(--s)/4);
  box-sizing: border-box;
  mask: url("data:image/svg+xml;utf8,<svg><path d='path_of_a_star_shape'/></svg>") 0/var(--s);
  appearance: none;
}
input[type="range"]::-webkit-slider-thumb{
  width: 1px;
  border-image: 
    conic-gradient(at calc(50% + var(--s)/4),#7b7b7b 50%,#fff220 0)
    fill 0//var(--s) calc(10*var(--s));
  appearance: none;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="WbeLEEQ" data-pen-title="CSS-Only  Rating Component (Click to update!)" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/WbeLEEQ">
  CSS-Only  Rating Component (Click to update!)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>


More detail: [A CSS-Only Star Rating Component and More!](https://css-tricks.com/a-css-only-star-rating-component-and-more-part-1/)