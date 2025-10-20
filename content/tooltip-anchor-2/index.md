---
layout: layouts/post.njk
title: Dynamic Tooltip Position with Anchor Positioning II
description: A tootlip that finds the best position to remain visible all the time
date: 2025-10-13
tags: posts
---

In [the previous post](/tooltip-anchor/), we created a tooltip that flips between two positions to remain visible. It's either on the top or the bottom. We can adjust the code to do the same with four positions (top, bottom, left, and right). And whatever the position of the tooltip, the tail will always point to the anchor.

{% image "./image.png", "anchor element with its tooltip shape" %}

```css
#anchor {
  position: absolute;
  anchor-name: --anchor;
}
#tooltip {
  --d: 1em;  /* distance between anchor and tooltip */
  --s: .8em; /* tail size */
  
  position: absolute; 
  position-anchor: --anchor;
  min-width: 10em;
  /* we place the tooltip at the top */
  position-area: top;
  bottom: var(--d);
  margin: var(--d);
  margin-bottom: 0;
  /* If top is not available with flip to bottom, 
     else if bottom is not available, we move to left, 
     else if left is not available, we move to right  */
  position-try: flip-block,--left,--right;
}
@position-try --left {
  position-area: left;
  right: var(--d);
  margin: var(--d);
  margin-right: 0;
}
@position-try --right {
  position-area: right;
  left: var(--d);
  margin: var(--d);
  margin-left: 0;
}
/* the tail */
#tooltip:before {
  content:"";
  position: absolute;
  z-index: -1;
  background: inherit;
  inset: calc(-1*var(--d));
  margin: inherit; /* the margin will do the magic and only show one part of the shape */
  /* the shape of the 4 arrows with one clip-path */
  clip-path: polygon(
    calc(50% - var(--s)) var(--d),50% .2em,calc(50% + var(--s)) var(--d),
    calc(100% - var(--d)) calc(50% - var(--s)), calc(100% - .2em) 50%,calc(100% - var(--d)) calc(50% + var(--s)),
    calc(50% + var(--s)) calc(100% - var(--d)),50% calc(100% - .2em),calc(50% - var(--s)) calc(100% - var(--d)),
    var(--d) calc(50% + var(--s)), .2em 50%,var(--d) calc(50% - var(--s))
  );
}
```

Here is an interactive demo where you can drag the anchor and see how the tooltip behaves:

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="QwyMrvG" data-pen-title="Follow me if you can! (drag the anchor)" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/QwyMrvG">
  Follow me if you can! (drag the anchor)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

If you click on "debug mode" you can see the global shape created with the pseudo-element that contains the four arrows.

The code can be simplified to the below if you don't want a `min-width` restriction:

```css
#anchor {
  position: absolute;
  anchor-name: --anchor;
}
#tooltip {
  --d: 1em;  /* distance between anchor and tooltip */
  --s: .8em; /* tail size */
  
  position: absolute; 
  position-anchor: --anchor;
  position-area: top;
  bottom: var(--d);
  margin: var(--d);
  margin-bottom: 0;
  position-try: flip-block,flip-start,flip-start flip-inline;
}

#tooltip:before {
  content:"";
  position: absolute;
  z-index: -1;
  background: inherit;
  inset: calc(-1*var(--d));
  margin: inherit; 
  clip-path: polygon(
    calc(50% - var(--s)) var(--d),50% .2em,calc(50% + var(--s)) var(--d),
    calc(100% - var(--d)) calc(50% - var(--s)), calc(100% - .2em) 50%,calc(100% - var(--d)) calc(50% + var(--s)),
    calc(50% + var(--s)) calc(100% - var(--d)),50% calc(100% - .2em),calc(50% - var(--s)) calc(100% - var(--d)),
    var(--d) calc(50% + var(--s)), .2em 50%,var(--d) calc(50% - var(--s))
  );
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="pvgpxwP" data-pen-title="Follow me if you can! (drag the anchor)" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/pvgpxwP">
  Follow me if you can! (drag the anchor)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>