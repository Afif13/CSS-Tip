---
layout: layouts/post.njk
title: Elastic/Bouncy Hover Effect
description: A few lines of modern CSS to create a fancy elastic effect on hover
date: 2026-02-03
tags: posts
---

Combining modern features such as [`shape()`](https://css-tricks.com/better-css-shapes-using-shape-part-1-lines-and-arcs/), [`sibling-index()/sibling-count()`](/element-index/), `linear()`, etc., to create a funny elastic effect on hover. There is no text duplication, but you need a monospace font and a wrapper per letter.

{% image "./image.png", "CSS-only elastic/bouncy effect on hover" %}

```html
<ul>
  <li>
    <a href="#"><span>A</span><span>b</span><span>o</span><span>u</span><span>t</span></a>
  </li>
</ul>
```

```css
@property --_s {
  syntax: "<number>";
  initial-value: 0;
  inherits: true;
}
ul li a {
  --h: .12em; /* control the elastic effect */
  --g: .15ch; /* the gap between letters */
  
  display: flex;
  gap: var(--g);
  font: bold 40px monospace;
  transition: --_s 1.5s linear(/* see the demo for the full code */);
}
ul li a:hover {
  --_s: 1;
  transition: --_s .3s;
}
ul li a span {
  offset: shape(from .5ch, 
      curve to calc((sibling-count() - 1)*(1ch + var(--g)) + .5ch) 50%
            with 30% calc(50% - var(--_s)*sibling-count()*var(--h))/
                 70% calc(50% - var(--_s)*sibling-count()*var(--h))
    ) calc(99.9%*(sibling-index() - 1)/(sibling-count() - 1));
}
```

Chrome-only for now:

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="xbOjoKR" data-pen-title="Elastic hover effect" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/xbOjoKR">
  Elastic hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Before using this on a production website, read this: [Barriers from Links with ARIA](https://adrianroselli.com/2026/01/barriers-from-links-with-aria.html) (TLDR: don't do it)