---
layout: layouts/post.njk
title: A Ribbon title to the edge of the screen
description: A magic border-image trick to add a ribbon shape to your title that extends to the endge of the screen
date: 2023-05-08
tags: posts
---

Add a ribbon style to your title that extend to the edge of the screen.
* Only one CSS property 🤩
* No extra element
* No pseudo-element
* No scrollbar issue

{% image "./image.png", "Titles having a ribbon style that extend to the left edge of the screen" %}

```css
.ribbon {
  border-image: 
     conic-gradient(
       from 45deg at calc(100% - 1lh),
       #0000 25%,#C7F464 0
     ) fill 0//0 0 0 100vw;
}
```


<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="rNqJYrZ" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/rNqJYrZ">
  Full screen Ribbon title</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

Related: [smashingmagazine.com/2024/01/css-border-image-property/](https://www.smashingmagazine.com/2024/01/css-border-image-property/)