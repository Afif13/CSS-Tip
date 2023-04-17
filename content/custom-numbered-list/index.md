---
layout: layouts/post.njk
title: Customize your numbered list
description: A simple CSS trick to customize your ol list
date: 2023-04-17
tags: posts
---

Use `@counter-style` to customize your `<ol>` list with a simple code
* No extra markup
* No pseudo-element
* No need for `counter()`
* Keep the default browser algorithm

{% image "./image.png", "A numbered list" %}

```css
@counter-style new-style {
  system: extends decimal;
  suffix: ") ";
  prefix: "(";
}
ol {
  list-style-type: new-style;
}
```


<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="GRYZeqr" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/GRYZeqr">
  Custom numbered list</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


