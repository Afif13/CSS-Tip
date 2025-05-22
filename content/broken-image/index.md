---
layout: layouts/post.njk
title: How to style a broken image
description: Give a nice visual touch to images that fail to load 
date: 2025-05-22
tags: posts
---

When an image fails to load the browser will simply show you the alt text but you can change this using a cool CSS trick. Broken images accept pseudo-elements such as `::before` and `::after` so we can tweak them to add a custom error message or any visual you want.

{% image "./image.png", "Custom error message for broken images" %}


```css
img {
  position: relative;
}
img::after {
  content: "We failed to load the image of \A'" attr(alt) "'\A 😞"/"";
  position: absolute;
  inset: 0;
  display: grid;
  place-items: center;
  text-align: center;
  border: 2px dashed;
  font: bold 1.6em/1.5 system-ui;
  white-space: pre-wrap;
}
```

The above style will not apply to correctly loaded images so no need for any specific selector to exclude them

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="QwbLwEb" data-pen-title="Style broken images" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/QwbLwEb">
  Style broken images</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>