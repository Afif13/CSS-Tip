---
layout: layouts/post.njk
title: Add a gradient overlay using border-image
description: One line of code to add a gradient overlay above your background
date: 2023-05-18
tags: posts
---

Do you want to add a gradient overlay above your background but you cannot edit the background property, add an extra element or use pseudo-element? 

You can do it with `border-image`!

Only one line of code and you have your overlay 🤩


{% image "./image.png", "A gradient overaly above a background-image" %}

```css
.container {
  border-image:
    linear-gradient(#0003,#000) /* your gradient here */
    50%/50%; /* no need to touch this, we always want 50% of slice 
                                                  and 50% border-width */
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="gOBBeyz" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/gOBBeyz">
  Gradient overlay using border-image</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


