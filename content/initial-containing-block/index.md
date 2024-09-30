---
layout: layouts/post.njk
title: Default behavior of position absolute
description: Know the meaning of initial containing block and its relation with position absolute 
date: 2024-09-30
tags: posts
---

Many have a wrong information about the default behavior of `position: absolute` element.

<i>"if an absolute positioned element has no positioned ancestors, it uses the body element"</i> NO, <strong>this is false!</strong>

The W3Schools page is showing a wrong information but the MDN page is showing the correct one.

<style>
  @media (width < 900px) {tr,td {display: block;}}
</style> 
<table>
  <tr>
    <td>{% image "./image.png", "Screenshot from W3schools showing a wrong information about position: absolute" %}</td>
    <td>{% image "./image1.png", "Screenshot from MDN showing a correct information about position: absolute" %}</td>
  </tr>
</table>

What is the [initial containing block](https://www.w3.org/TR/CSS22/visudet.html#containing-block-details)?

It's a rectangle having the same dimension as the viewport (full width/height) and anchored at the canvas origin (moves on scroll). In other words, it's similar to the viewport but moves if we have scrolling.

Here is a demo to illustrate:

<p class="codepen" data-height="350" data-default-tab="result" data-slug-hash="bGXVMjp" data-pen-title="Default behavior of position: absolute" data-preview="true" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/bGXVMjp">
  Default behavior of position: absolute</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

The absolute element is not using the body (blue rectangle) nor the html (red rectangle) but that green rectangle having the viewport dimension and moving on scroll. That's the initial containing block!
