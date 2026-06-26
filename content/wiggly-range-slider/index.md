---
layout: layouts/post.njk
title: Wiggly/Wavy Input Range Slider
description: Say goodbye to the boring straight range slider and say hello to the fancy wiggly range slider
date: 2026-06-23
tags: posts
---

Straight range sliders are boring, right? Let's, instead, draw the lines by hand and get some wiggly/wavy range sliders!

{% image "./image.png", "CSS-only wavy/wiggly range slider" %}

A fancy demo powered by `border-shape`, Scroll-Driven Animations, `@property`, and more!

The HTML code is nothing but the native `<input>` element. No extra element and, of course, no JavaScript.

```html
<input type="range" step=".2" max="20" value="10">
<input type="range" value="80">
<input type="range" min="-10" step=".1" max="10" value="-5">
```

⚠️ A Chrome-only experience ⚠️

<p class="codepen" data-height="450" data-pen-title="Wiggly/Wavy Range Slider" data-preview="true" data-default-tab="result" data-slug-hash="zxNwjKa" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zxNwjKa">
  Wiggly/Wavy Range Slider</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

You can easily control everything by adjusting a few CSS variables:

```css
input[type="range"] {
  --s: 30px; /* size/height of the slider */
  --t: 45px; /* size of the thumb*/
  --l: 6px; /* line thickness */
  --c: #547980; /* main color */
  --p: shape(...); /* shape of the line  */
}
```

You can get the line's shape using my [wavy divider generator](https://css-generators.com/wavy-divider/). Pick the border-only configuration, select "top", and set the size to 100%. Then adjust the granularity and click generate! 

{% image "./image1.png", "Screenshot of my wavy divider generator" %}