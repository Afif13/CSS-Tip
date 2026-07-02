---
layout: layouts/post.njk
title: background-clip is getting an upgrade!
description: Learn about the new values of the background-clip property
date: 2026-07-02
tags: posts
---

As we saw in [a pervious post](/border-gradient/), the new value `border-area` of `background-clip` allows us to define a gradient border with simple code.

```css
.gradient-border {
  border: 10px solid #0000;
  background: linear-gradient(#90e0ef,#f4a261) border-area; 
}
```

{% image "./image.png", "CSS gradient border with border-radius" %}

That value can also be combined with the `text` value to apply the gradient to the text. A simple way to have a text and border gradient while leaving the background transparent.

```css
.gradient-text-border {
  border: 10px solid #0000;
  color: #0000;
  background: linear-gradient(#90e0ef,#f4a261) border-area text; 
}
```

{% image "./image1.png", "CSS-only text and border gradient" %}

⚠️ Support is still limited (Chrome-only starting from V150) ⚠️

<p class="codepen" data-height="350" data-pen-title="Gradient text &amp;amp; border" data-preview="true" data-default-tab="result" data-slug-hash="xbgPEWL" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/xbgPEWL">
  Gradient text &amp; border</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

The longhand version looks like the one below. 

```css
.gradient-text-border {
  border: 10px solid #0000;
  color: #0000;
  background-image: linear-gradient(#FF4E50,#40C0CB);
  background-clip: border-area text;  /* Two values */
  background-origin: border-box; 
}
```

Note that `background-origin` is by default equal to `border-box` in the shorthand version when specifying `border-area`. In the longhand version, you need to set it explicitly to `border-box`; otherwise, it defaults to `padding-box`, which makes the gradient a bit off.