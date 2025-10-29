---
layout: layouts/post.njk
title: Dynamic Tooltip Position with Anchor Positioning III
description: Another idea of a tooltip following its anchor 
date: 2025-10-20
tags: posts
---

Here is another idea of implementation (after the [first](/tooltip-anchor/) and [second](/tooltip-anchor-2/) ones), where the tooltip adjusts its position to remain visible and follow its anchor. This time, I am considering the corner positions. 

{% image "./image.png", "CSS-only tooltip and anchor element" %}

```css
#anchor {
  position: absolute;
  anchor-name: --anchor;
}
#tooltip {
  --d: .5em; /* distance between anchor and tooltip */
  --s: .8em; /* tail size & border radius */
  
  position: absolute;
  border-radius: var(--s);
  min-width: 10em;
  position-anchor: --anchor;
  position-area: top left;
  margin: var(--d);
  position-try: flip-inline,flip-block,flip-block flip-inline; 
  anchor-name: --tooltip;
  clip-path: inset(calc(-1*var(--d)));
}

#tooltip:before,
#tooltip:after {
  content: "";
  position: fixed;
  --_m: calc((sqrt(2) - 1)*var(--s));
  width:  calc(anchor-size(--tooltip width)  + var(--d) - var(--_m));
  height: calc(anchor-size(--tooltip height) + var(--d) - var(--_m));
  z-index: -1;
  background: inherit;
  position-anchor: --anchor;
  position-try: flip-block flip-inline;
}
#tooltip:before {
  position-area: top left;
  margin: calc(var(--_m) + var(--d)) 0 0 calc(var(--_m) + var(--d));
  clip-path: polygon(
    var(--d) calc(var(--s) + var(--d)),0 0,calc(var(--s) + var(--d)) var(--d),
    calc(100% - var(--d)) calc(100% - var(--d) - var(--s)),100% 100%,calc(100% - var(--d) - var(--s)) calc(100% - var(--d)))
}
#tooltip:after {
  position-area: top right;
  margin: calc(var(--_m) + var(--d)) calc(var(--_m) + var(--d)) 0 0;
  clip-path: polygon(
    var(--d) calc(100% - var(--s) - var(--d)),0 100%,calc(var(--s) + var(--d)) calc(100% - var(--d)),
    calc(100% - var(--d)) calc(var(--d) + var(--s)),100% 0,calc(100% - var(--d) - var(--s)) var(--d))
}
```

Here is an interactive demo where you can drag the anchor and see how the tooltip behaves:

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="yyepRJM" data-pen-title="Follow me if you can! (drag the anchor)" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yyepRJM">
  Follow me if you can! (drag the anchor)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Click "debug mode" To see how both pseudo-elements are creating the tails.

