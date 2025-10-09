---
layout: layouts/post.njk
title: Dynamic Tooltip Position with Anchor Positioning
description: A tootlip that follows its anchor while adjusting the position of its tail
date: 2025-10-06
tags: posts
---

With anchor positioning, we can anchor an element to another and also ensure it remains visible on the screen regardless of the anchor's position. Now, imagine the element you want to anchor is a tooltip. What about its tail? We can also adjust its position to always point to the anchor.

{% image "./image.png", "anchor element with its tooltip shape" %}

```css
#anchor {
  position: absolute;
  anchor-name: --anchor;
}
#tooltip {
  --distance: 1em; /* distance between anchor and tooltip  */
  --size: 1.2em;   /* control tail size */
  
  position: absolute; 
  position-anchor: --anchor;
  /* place tooltip at top */
  bottom: calc(anchor(top) + var(--distance));
  justify-self: anchor-center;
  /* if it doesn't fit, fall back to bottom */
  position-try-fallbacks: --to-bottom;
  margin: var(--distance) 0 0; /* the margin is inherited by the pseudo element, it does nothing here */
  anchor-name: --tooltip;
}
@position-try --to-bottom {
  bottom: auto;
  top: calc(anchor(bottom) + var(--distance));
  margin: 0 0 var(--distance); /* we update the margin for the pseudo element */
}

#tooltip:before {
  content:"";
  position: fixed;
  z-index: -1;
  width: var(--size);
  background: inherit;
  /* vertical position from tootlip  */
  top:    calc(anchor(--tooltip top   ) - var(--distance));
  bottom: calc(anchor(--tooltip bottom) - var(--distance));
  /* horizontal position from anchor */
  left: calc(anchor(--anchor center) - var(--size)/2);
  margin: inherit; /* this will do the magic, it will hide either the top or the bottom of the shape */
  /* the arrow shape */
  clip-path: /* .... */;
}
```

Here is an interactive demo where you can drag the anchor and see how the tooltip behaves:

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="RNrKmpY" data-pen-title="Follow me if you can! (drag the anchor)" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/RNrKmpY">
  Follow me if you can! (drag the anchor)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>


Click the "debug mode" to understand the trick. Both arrows are always visible, but the margin will update the position to simulate the "hide" effect. 

In case you are wondering, the properties allowed inside `@position-try` are limited, which is why I need to rely on this hack until we have better support for [`anchored queries`](https://drafts.csswg.org/css-anchor-position-2/#container-rule-anchored).