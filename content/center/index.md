---
layout: layouts/post.njk
title: 100 ways to center an element horizontally and vertically
description: Explore all the possible ways to center a single element within a container
date: 2025-09-16
tags: posts
---

Centering in CSS is pretty easy nowadays. We have numerous methods to do it, but how many exactly? I did the count, and I was able to reach 100 different ways!

[css-generators.com/center/](https://css-generators.com/center/)

The list includes old and obsolete methods (that you should not use), but it was a fun exercise trying to enumerate all the possibilities.

<h2>Which method should I use?</h2>

I don't recommend choosing a single method to always use. Instead, consider the layout you are working with and select the appropriate code. It's crucial to understand what each code is doing because not all of them are the same. To help you with this, you can check [my exploration to understand the fundamentals of alignment in CSS](https://css-tip.com/explore/alignment/).

That being said, here are my favorite methods for centering <strong>a single element horizontally and vertically</strong> for each type of layout.


```css
.container { 
  display: block;
  align-content: center;
  justify-items: center; /* the support is still not good for this one */
}
```

```css
.container {
  display: grid;
  place-content: center;
}
```

```css
.container {
  display: flex;
  flex-wrap: wrap;
  place-content: center;
}
```

One advantage of these methods is that they can also be used to center multiple items (under certain conditions). For this reason, I am considering only the container (and not the item) when defining the alignment properties.

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="GgpVweO" data-pen-title="Centering multiple items" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/GgpVweO">
  Centering multiple items</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

The flex approach is interesting because it's the only one that places the items horizontally and switches to a vertical configuration when the container is narrowed. 