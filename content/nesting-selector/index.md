---
layout: layouts/post.njk
title: Be careful when using the nesting selector (&)
description: The "&" selector is not the same in CSS and Sass so use it carefully
date: 2024-02-19
tags: posts
---

CSS Nesting is cool and using the "&amp;" is a lifesaver BUT be careful. There's a gotcha!

⚠️ "&amp;" in CSS is different from the one in Sass ⚠️

Your Sass code won't work the same way if you use it as a CSS code.

The below code won't give the same result when used with CSS Nesting and Sass

```css
section {
   p {
    font-size: 20px;
    .main & {
      color: red;
    }
  }
}
```

{% image "./image.png", "Difference between Sass and CSS when using nesting" %}

CSS Nesting introduces the `:is()` part which make the selection different: [Select any element that is descendant of .main AND is “section p” (p element descendant of section)]

Here are two demos using the same code but with a different setting.

* Using native CSS

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="zYbbmbb" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zYbbmbb">
  CSS nesting code</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

* Using Sass

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="zYbbMKg" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zYbbMKg">
  Sass  nesting code</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

The nesting selector can be desugared by replacing it with the parent style rule’s selector, wrapped in an `:is()` selector. <sup>[ref](https://www.w3.org/TR/css-nesting-1/#nest-selector)</sup>
