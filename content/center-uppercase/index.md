---
layout: layouts/post.njk
title: Perfectly center an uppercase text
description: One line of code and you can have a true centering for any uppercase text
date: 2025-02-24
tags: posts
---

Are you tired of the unwanted spaces above and below your text? One line of code can fix this and you can have a perfect centering for your uppercase text.

{% image "./image.png", "Vertically center uppercase text" %}

```css
.text {
  text-box: cap alphabetic;
}
```

Chrome-only for now

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="WbNxPzq" data-pen-title="Perfectly centered uppercase!" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/WbNxPzq">
  Perfectly centered uppercase!</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


Another interesting one in case you have a lowercase text (without ascender or descender).

```css
.text {
  text-box: ex alphabetic;
}
```

{% image "./image2.png", "Vertically center lowercase text" %}

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="yyLaNVd" data-pen-title="Perfectly centered lowercase!" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yyLaNVd">
  Perfectly centered lowercase!</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>