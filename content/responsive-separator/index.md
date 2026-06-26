---
layout: layouts/post.njk
title: Responsive Separator for Horizontal List
description: Modern CSS solves a very old design pattern with a few lines of code
date: 2026-06-26
tags: posts
---

Separating a horizontal list of items with a divider is a common design pattern. The tricky part is making sure we have separators only between adjacent items, never at the beginning or the end of the row/line.

{% image "./image.png", "CSS-only responsive list separator" %}

There are many hacky ways to solve this, but the new [Gap Decoration feature](https://master.dev/blog/lets-play-with-gap-decorations/) offers a simple, modern solution. No more hacks and only a few lines of code to get the shape of the divider you want.

```css
.vertical-line {
  column-rule: 3px solid #c1121f; /* width = 3px */
  rule-inset: calc(.5lh - .75em/2); /* height = .75em */
}
.horizontal-line {
  column-rule: .75em solid #c1121f; /* width = .75em */
  rule-inset: calc(.5lh - 4px/2); /* height = 4px */
}
.square {
  --s: 10px; /* size */
  column-rule: var(--s) solid #c1121f;
  rule-inset: calc(.5lh - var(--s)/2);
}
.circle {
  --s: 10px; /* size */
  column-rule: var(--s) dotted #c1121f;
  rule-inset: calc(.5lh - var(--s)/2);
}
```

Here is an interactive demo where you can adjust the alignment, resize the container, and see how the divider behaves.

⚠️ Chromium-only for now ⚠️

<p class="codepen" data-height="600" data-pen-title="Responsive Separator for Horizontal List" data-preview="true" data-default-tab="result" data-slug-hash="wBgqwMJ" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/wBgqwMJ">
  Responsive Separator for Horizontal List</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Until better support, check this: [Responsive Separator for Horizontal List](https://stackoverflow.com/q/37052659/8620333)