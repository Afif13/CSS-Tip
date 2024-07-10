---
layout: layouts/post.njk
title: Border gradient with border-radius
description: The modern way to add gradient to borders while having rounder corners
date: 2024-07-10
tags: posts
---

Save this code for the future! It will be the easiest way to add a gradient coloration to borders while having rounded corners.
* No pseudo-element
* One gradient layer
* Transparent background

{% image "./image.png", "CSS gradient border with border-radius" %}

⚠️ There is no implementation yet, but it's good to know.

```css
.gradient-border {
  border: 5px solid #0000;
  border-radius: 25px;
  background: linear-gradient(#FF4E50,#40C0CB) border-box;
  background-clip: border-area; /* The new added value */
}
```

Related: [[css-backgrounds] background-clip: border-area](https://github.com/w3c/csswg-drafts/issues/9456)

----

Until then, you can rely on CSS mask and pseudo-element if you want transparency

```css
.gradient-border {
  border-radius: 25px;
  position: relative;
}
.gradient-border:before {
  content: "";
  position: absolute;
  inset: 0;
  padding: 5px; /* border length  */
  background: linear-gradient(#FF4E50,#40C0CB);
  border-radius: inherit;
  mask: conic-gradient(#000 0 0) content-box exclude,conic-gradient(#000 0 0);
}
```

Or two background layers if transparency is not required:

```css
.gradient-border {
  border: 5px solid #0000;
  border-radius: 25px;
  background: 
    conic-gradient(#fff /* the background color */ 0 0) padding-box,
    linear-gradient(#FF4E50,#40C0CB) border-box;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="ZEdYKvo" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZEdYKvo">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>