---
layout: layouts/post.njk
title: Color shades using color-mix()
description: Mix your color with black or white to create color shades
date: 2023-03-28
tags: posts
---

Use the new `color-mix()` to create different shades from one color.

Mix with ⚫️ black for a darker color and ⚪️ white for a lighter color

```css
html {
  --color: #8A9B0F; /* the main color */
  --color-light: color-mix(in srgb,var(--color),#fff 25%);
  --color-dark:  color-mix(in srgb,var(--color),#000 25%);
}
```

{% image "./color-shades.png", "3 color shades from one color" %}

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="ExeMOPV" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ExeMOPV">
  Color shades using  color-mix()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

## Related Links

* [https://developer.chrome.com/articles/high-definition-css-color-guide/](https://developer.chrome.com/articles/high-definition-css-color-guide/)
* [https://www.w3.org/TR/css-color-5/#color-mix](https://www.w3.org/TR/css-color-5/#color-mix)


