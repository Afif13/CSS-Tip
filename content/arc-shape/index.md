---
layout: layouts/post.njk
title: Arc shape with rounded edges
description: a few lines of modern CSS to create an arc shape with rounded edges
date: 2024-08-07
tags: posts
---

Create an [arc shape](https://css-shape.com/arc/) with rounded edges using a few lines of CSS
* Single element (no pseudo-element)
* Less than 10 CSS declarations
* Supports gradient coloration
* Optimized with CSS variables


{% image "./image.png", "A 3D shine animation on image" %}

```css
.arc {
  --b: 30px; /* the boder thickness */
  --a: 220deg; /* control the progression */
  
  width: 200px;
  aspect-ratio: 1;
  padding: var(--b);
  box-sizing: border-box;
  border-radius: 50%;
  background: linear-gradient(#CC333F,#8A9B0F);
  --_g:/var(--b) var(--b) no-repeat
    radial-gradient(50% 50%,#000 calc(100% - 1px),#0000);
  mask:
    top var(--_g),
     calc(50% + 50%*sin(var(--a))) 
     calc(50% - 50%*cos(var(--a))) var(--_g),
    linear-gradient(#0000 0 0) content-box intersect,
    conic-gradient(#000 var(--a),#0000 0);
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="oNrwRqP" data-pen-title="Arc shape with rounded edges" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/oNrwRqP">
  Arc shape with rounded edges</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More CSS Shapes: [css-shape.com](https://css-shape.com/)