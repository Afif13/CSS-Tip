---
layout: layouts/post.njk
title: Color switch using color-mix()
description: Use the new color-mix() to create a simple color switch
date: 2023-03-27
tags: posts
---

Use the new `color-mix()` function to create a color switch with a compact code

* No color duplication
* Define your colors using one variable
* Easy switch between colors
* Suitable for dark/light mode

```css
:root {
  --colors: black, white; /* define your colors like an array */
  --i: 0; /* black text / white background */
  
  --_color:    color-mix(in hsl, var(--colors) calc(var(--i)*100%));
  --_bg-color: color-mix(in hsl, calc(var(--i)*100%) var(--colors));
}
@media (prefers-color-scheme: dark) {
  :root {
    --i: 1; /* white text / black background */
  }
}

body {
  color: var(--_color);
  background: var(--_bg-color);
}
```

<p class="codepen" data-height="350" data-default-tab="result" data-slug-hash="XWPGWPp" data-preview="true" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWPGWPp">
  A color switch using color-mix()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

## Related Links

* [https://developer.chrome.com/articles/high-definition-css-color-guide/](https://developer.chrome.com/articles/high-definition-css-color-guide/)
* [https://www.w3.org/TR/css-color-5/#color-mix](https://www.w3.org/TR/css-color-5/#color-mix)