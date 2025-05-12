---
layout: layouts/post.njk
title: SVG to CSS Shape Converter
description: The easiest way to convert an SVG shape into a CSS one
date: 2025-05-12
tags: posts
---

Do you want to convert an SVG code into CSS? Check my online generator: [css-generators.com/svg-to-css](https://css-generators.com/svg-to-css/)

It will transform a shape created using `<path d="...">` into a CSS code using `clip-path: shape()`. It's responsive, and the HTML code is a single element. No need to care about the viewBox, the generator will automatically find the smallest rectangle in which the shape fits.

Example of SVG path:

```html
<path d="M199.6,18.9c-4.3-8.9-12.5-16.4-22.3-17.8c-11.9-1.7-23.1,5.4-32.2,13.2c-9.1,7.8-17.8,16.8-29.3,20.3c-20.5,6.2-41.7-7.4-63.1-7.5C38.7,27,24.8,33,15.2,43.3c-35.5,38.2-0.1,99.4,40.6,116.2c32.8,13.6,72.1,5.9,100.9-15c27.4-19.9,44.3-54.9,47.4-88.6c0.2-2.7,0.4-5.3,0.5-7.9C204.8,38,203.9,27.8,199.6,18.9z"></path>
```

It will get converted to:

```css
.shape {
  aspect-ratio: 1.233;
  clip-path: shape(from 97.54% 10.91%,curve by -10.93% -10.76% with -2.11% -5.38%/-6.13% -9.91%,curve by -15.78% 7.98% with -5.83% -1.03%/-11.32% 3.26%,curve by -14.36% 12.27% with -4.46% 4.71%/-8.72% 10.15%,curve by -30.93% -4.53% with -10.05% 3.75%/-20.44% -4.47%,curve to 7.15% 25.66% with 18.67% 15.81%/11.86% 19.43%,curve by 19.9% 70.23% with -17.4% 23.09%/-0.05% 60.08%,curve by 49.46% -9.07% with 16.08% 8.22%/35.34% 3.57%,curve by 23.23% -53.55% with 13.43% -12.03%/21.71% -33.18%,curve by 0.25% -4.77% with 0.1% -1.63%/0.2% -3.2%,curve to 97.54% 10.91% with 100.09% 22.46%/99.64% 16.29%,close);
}
```

Then you can apply the shape to any element of any size:

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="ZYYmNGK" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZYYmNGK">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>