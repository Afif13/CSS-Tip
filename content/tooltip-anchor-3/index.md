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
  position-anchor: --anchor;
  position-area: top left;
  margin: var(--d);
  position-try: flip-inline,flip-block,flip-block flip-inline;
  clip-path: inset(0) margin-box;
}

#tooltip:before {
  content: "";
  position: fixed;
  position-area: center;
  width:  calc(anchor-size(width) +  2*(var(--d) + var(--s)));
  height: calc(anchor-size(height) + 2*(var(--d) + var(--s)));
  background: inherit;
  z-index: -1;
  position-anchor: --anchor;
  clip-path: polygon(0 0,0 100%,100% 100%,100% 0,0 0,var(--s) 0,calc(100% - var(--s)) 0,calc(100% - var(--s) - var(--d)) calc(var(--d) + var(--s)),100% var(--s),100% calc(100% - var(--s)), calc(100% - var(--s) - var(--d)) calc(100% - var(--s) - var(--d)),calc(100% - var(--s)) 100%,var(--s) 100%,calc(var(--s) + var(--d)) calc(100% - var(--s) - var(--d)),0 calc(100% - var(--s)), 0 var(--s),calc(var(--s) + var(--d)) calc(var(--s) + var(--d)),var(--s) 0);
}
```

Here is an interactive demo where you can drag the anchor and see how the tooltip behaves:

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="yyepRJM" data-pen-title="Follow me if you can! (drag the anchor)" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yyepRJM">
  Follow me if you can! (drag the anchor)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>



