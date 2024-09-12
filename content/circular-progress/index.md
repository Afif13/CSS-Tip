---
layout: layouts/post.njk
title: Circular progress using scroll-driven animations
description: Transforming the native progress element into a circular one using scroll-driven animations
date: 2024-07-04
tags: posts
---

Transforming the native progress element into a circular one.
* No extra elements (only the `<progress>` tag)
* No Magic Numbers
* Everything is controlled by the "max" and "value" attributes
* Powered by Scroll-Driven animations & `@property`

{% image "./image.png", "CSS-only circular progress element" %}

It's a Chrome-only experimentation:

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="PovMVjJ" data-pen-title="Circular progress element using scroll-driven animation" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/PovMVjJ">
  Circular progress element using scroll-driven animation</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

Related: [Progress element with a tooltip](/progress-with-tooltip/)