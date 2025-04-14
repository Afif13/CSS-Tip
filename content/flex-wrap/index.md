---
layout: layouts/post.njk
title: The unknown behavior of flex-wrap
description: flex-wrap doesn't only control the wrapping of items but also affects the alignment
date: 2025-04-14
tags: posts
---

`flex-wrap: wrap` allows items to wrap onto multiple lines but it has another function. It transforms your flex container from a single-line to a multi-line container even if at the end you have only one flex line. This means we can use `align-content` to align the content.

In other words, you need to use `flex-wrap: wrap` to align the content using `align-content` even if there is no wrapping.

{% image "./image.png", "flex-wrap & align-content" %}

It's different from `align-items` which aligns the items inside the line whereas `align-content` aligns the whole line. Here is an interactive demo to see the behavior of each property:

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="EaxBevN" data-pen-title="flex-wrap &amp;amp; alignment" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/EaxBevN">
  flex-wrap &amp; alignment</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>