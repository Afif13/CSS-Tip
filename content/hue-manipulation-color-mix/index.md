---
layout: layouts/post.njk
title: Hue manipulation using color-mix()
description: Use the new color-mix() to manipulate the Hue of a color in the HSL color space
date: 2023-03-29
tags: posts
---

Use the new `color-mix()` to manipulate the Hue of a color in the HSL color space

```css
.box {
  --color: red; 
  --h: 0; /* angle (from 0 to 360 without unit) */
  
  --new-color: 
    color-mix(in hsl longer hue, 
      var(--color), var(--color) calc(var(--h)*1%/3.6)
    );
}
```

The same can be done using relative colors but the support is still low:

```css
.box {
  --color: red; 
  --h: 0; /* angle (from 0 to 360 without unit) */
  
  --new-color: hsl(from var(--color) calc(h + var(--h)*1deg) s l)
}
``` 

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="VwGNQEv" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/VwGNQEv">
  hue manipulation using color-mix()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

## Related Links

* [https://developer.chrome.com/articles/high-definition-css-color-guide/](https://developer.chrome.com/articles/high-definition-css-color-guide/)
* [https://www.w3.org/TR/css-color-5/#color-mix](https://www.w3.org/TR/css-color-5/#color-mix)
