---
layout: layouts/post.njk
title: A Fancy Hover Effect For Your Avatar
description: Create a stunning "Pop out" hover effect using modern CSS
date: 2023-08-11
tags: posts
---

Add a nice "Pop out" hover effect to your avatar using a minimalist code
* No extra element (only the `<img>` tag)
* No pseudo-element
* Less than 20 declarations
* Optimized with CSS variables


{% image "./image.png", "A pop out hover effect to image" %}

```css
img {
  --s: 280px; /* image size */
  --b: 5px; /* border thickness */
  --c: #C02942; /* border color */
  --f: 1; /* initial scale */
  
  width: var(--s);
  aspect-ratio: 1;
  padding-top: calc(var(--s)/5);
  border-radius: 0 0 999px 999px;
  --_g: 50%/calc(100%/var(--f)) 100% no-repeat content-box;
  --_o: calc((1/var(--f) - 1)*var(--s)/2 - var(--b));
  outline: var(--b) solid var(--c);
  outline-offset: var(--_o);
  background: 
    radial-gradient(
      circle closest-side,
      #ECD078 calc(99% - var(--b)),var(--c) calc(100% - var(--b)) 99%,#0000
     ) var(--_g);
  mask:
    linear-gradient(#000 0 0) no-repeat
     50% calc(1px - var(--_o)) / calc(100%/var(--f) - 2*var(--b) - 2px) 50%,
    radial-gradient(circle closest-side,#000 99%,#0000) var(--_g);
  transform: scale(var(--f));
  transition: .5s;
}
img:hover {
  --f: 1.35; /* hover scale */
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="MWBjraa" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/MWBjraa">
  Fancy hover effect on avatar</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [css-tricks.com/a-fancy-hover-effect-for-your-avatar/](https://css-tricks.com/a-fancy-hover-effect-for-your-avatar/)