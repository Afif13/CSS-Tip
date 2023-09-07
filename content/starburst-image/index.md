---
layout: layouts/post.njk
title: Starburst images with rotation
description: Use clip-path to turn your image into a starburst shape
date: 2023-09-07
tags: posts
---

Place your image inside a Starburst shape with a cool rotation 🤩
* No extra element (only the `<img>` tag)
* Powered by clip-path

Get the code in no time using an [Online Generator for Starburst Shape](https://css-generators.com/starburst-shape/)


{% image "./image.png", "Images with Starburst shapes" %}

```css
img {
  aspect-ratio: 1;
  animation: spike1 .8s linear infinite;
}
/* The below are generated using: https://css-generators.com/starburst-shape/
   Define the number of spikes then: 
   - Place the rotation at min and copy the value on the 0% state
   - Place the rotation at max and copy the value on the to state
   That's all!
*/
@keyframes spike1 {
  0% {
    clip-path: /* from the generator */;
  }
  to {
    clip-path: /* from the generator */;
  }
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="dywNWJp" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dywNWJp">
  Starburst rotating images</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>