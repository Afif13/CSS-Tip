---
layout: layouts/post.njk
title: Progress element with a tooltip
description: Adding a tooltip to the native progress element showing the precentage of progress
date: 2024-09-10
tags: posts
---

Adding a tooltip to the native progress element showing the percentage of progress.
* No extra elements (only the `<progress>` tag)
* No inline CSS
* Everything is controlled by the "max" and "value" attributes
* Powered by Scroll-Driven animations, anchor positioning & `@property`

{% image "./image.png", "CSS-only progress element with a tooltip" %}

It's a Chrome-only experimentation:

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="YzoBmLb" data-pen-title="Upgrading the progress element with modern CSS (Chrome only)" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/YzoBmLb">
  Upgrading the progress element with modern CSS (Chrome only)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Here is another version with a cool animation:

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="JjQVYgJ" data-pen-title="Progress element with tooltip II (Chrome only)" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/JjQVYgJ">
  Progress element with tooltip II (Chrome only)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

Related : [Circular progress using scroll-driven animations](/circular-progress/)