---
layout: layouts/post.njk
title: Indent each line of your text
description: A new value of text-indent that allows you to indent each line of text
date: 2024-11-04
tags: posts
---

Do you know that `text-indent` can take an extra value `each-line`? It allows you to have an indentation after each line! Useful if you rely on `<br>` to add new lines.


```css
p {
  text-indent: 2em each-line;
}
```

{% image "./image.png", "text-indent each-line" %}

⚠️ It has limited support. Only Firefox and Safari for now ⚠️


<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="MWNBrab" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/MWNBrab">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>