---
layout: layouts/post.njk
title: How to use the "auto" value with clamp()
description: A CSS trick to use clamp() with sizing values like auto, min-content, max-content, etc 
date: 2026-02-05
tags: posts
---

If you have tried the code below, you know it doesn't work:

```css
.box {
  width: clamp(200px, auto, 400px);
}
```

`clamp()` accepts only calculations, and values such as `auto`, `min-content`, and `max-content` aren't allowed. They make the entire value invalid. 

With the new `calc-size()`, we can allow such values within `clamp()`.


```css
.box {
  width: calc-size(auto,clamp(200px, size, 400px));
  /* same as clamp(200px, auto, 400px) */
}
```

The first argument of `calc-size()` can be any calculation or a sizing keywords. The second argument is a calculation where `size` refers to the first argument. 


You can have endless combinations.

```css
.box {
  width: calc-size(max-content,clamp(size, 70%, 600px)); 
  /* same as clamp(max-content,70%, 600px) */
  width: calc-size(max-content,clamp(300px, 80%, 2*size)); 
  /* same as clamp(300px, 80%, 2*max-content) */
  width: calc-size(min-content,clamp(size + 50px, 100% - 40px, 700px));
  /* same as clamp(min-content + 50px, 100% - 40px, 700px) */
  width: calc-size(max-content,clamp(size,80%, 2*size))
  /* same as clamp(max-content, 80%, 2*max-content) */
}
```

⚠️ Limited support (Chrome-only for now)

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="gbMzWZK" data-pen-title="clamp() with keyword values" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/gbMzWZK">
  clamp() with keyword values</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>
