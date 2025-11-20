---
layout: layouts/post.njk
title: Dynamic Tooltip Position with Anchor Positioning IV
description: A tooltip with a stretchy arrow that follows its anchor
date: 2025-11-20
tags: posts
---

Another demo using Anchor Positioning and Tooltips. This time, the tail will have a stretchy behavior when the tooltip gets closer to the edges.

{% image "./image.png", "CSS-only tooltip with stretchy arrow" %}

```css
#anchor {
  position: absolute;
  anchor-name: --anchor;
}
#tooltip {
  --d: 1.2em; /* distance between tooltip and anchor */
  --s: 1.5em; /* size of the tail */ 
  
  position: absolute;
  position-anchor: --anchor;
  bottom: var(--d);
  position-area: top;
  margin: var(--d) var(--d) 0;
  position-try: flip-block; 
  anchor-name: --tooltip;
}

#tooltip:before,
#tooltip:after {
  content:"";
  position: fixed;
  background: inherit;
  inset-block: calc(anchor(--tooltip inside) - var(--d));
  left: calc(anchor(--anchor center) - var(--s)/2);
  right: calc(anchor(--tooltip center) - var(--s)/2);
  margin-block: inherit;
  clip-path: polygon(min(50%,100% - var(--s)) var(--d),calc(var(--s)/2) 0,100% var(--d),100% calc(100% - var(--d)),calc(var(--s)/2) 100%,min(50%,100% - var(--s)) calc(100% - var(--d)));
}
#tooltip:after {
  left: calc(anchor(--tooltip center) - var(--s)/2);
  right: calc(anchor(--anchor center) - var(--s)/2);
  clip-path: polygon(max(50%,var(--s)) var(--d),calc(100% - var(--s)/2) 0,0 var(--d),0 calc(100% - var(--d)),calc(100% - var(--s)/2) 100%,max(50%,var(--s)) calc(100% - var(--d)));
}
```

Drag the anchor in the demo below to see how the tooltip and its tail behave:

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="ogxeKQY" data-pen-title="Follow me if you can! (drag the anchor)" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/ogxeKQY">
  Follow me if you can! (drag the anchor)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>


