---
layout: layouts/post.njk
title: Breakout Background using Modern CSS
description: Use border-shape or border-image to extend the background color to the edge of the screen
date: 2026-08-05
tags: posts
---

Do you want to extend the background color of your element to the edge of the screen? A simple code using `border-shape` or `border-image`, and it's done!


{% image "./image.png", "CSS-only breakout background color" %}


```css
.breakout-background {
  border-shape: inset(0 -100vw) circle(0);
  border-color: #faa307;
}
```

⚠️ (Chromium only for now) ⚠️

<p class="codepen" data-height="650" data-pen-title="Breakout background using border-shape" data-preview="true" data-default-tab="result" data-slug-hash="OPWdzNO" data-user="t_afif" style="height: 650px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/OPWdzNO">
  Breakout background using border-shape</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

### How Does it Work?

`border-shape` accepts two shape values (outer and inner); the border is rendered as the area between them. The outer shape is a rectangle that extends to the edge of the screen, and the inner shape is a zero-radius circle placed at the center. The idea is to make sure the inner shape is "nothing" to end with the outer shape fully filled.

Here is a demo with a transition on hover to better understand what's going on.

```css
.breakout-background {
  border-shape: inset(0) circle(20%);
  border-color: #faa307;
}
.breakout-background:hover {
  border-shape: inset(0 -100vw) circle(0);
}
```

<p class="codepen" data-height="550" data-pen-title="Hover to extend!" data-preview="true" data-default-tab="result" data-slug-hash="jEydYmQ" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/jEydYmQ">
  Hover to extend!</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Until better support, you can rely on [`border-image` and one line of code](https://css-tip.com/overflowing-background/):

```css
.breakout-background {
  border-image: conic-gradient(#faa307 0 0) fill 0//0 100vw;
}
```

A line of code that we can optimize using the new `image()` function (more detail: [How to correctly define a one-color gradient](https://css-tip.com/one-color-gradient/))

```css
.breakout-background {
  border-image: image(#faa307) fill 0//0 100vw;
}
```

<p class="codepen" data-height="650" data-pen-title="Breakout background using border-image" data-preview="true" data-default-tab="result" data-slug-hash="xbgMpZx" data-user="t_afif" style="height: 650px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/xbgMpZx">
  Breakout background using border-image</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>