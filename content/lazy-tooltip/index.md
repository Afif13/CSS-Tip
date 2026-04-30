---
layout: layouts/post.njk
title: The Lazy Tooltip Follower
description: A fun demo illustrating a tooltip that follows its anchor, but slowly
date: 2026-04-29
tags: posts
---

Another demo featuring [tooltips](https://css-generators.com/tooltip-speech-bubble/) and Anchor Positioning. This time, I am relying on the fact that you can apply a transition to the inset properties to create a "lazy" tooltip follower. A tooltip that follows the anchor when you drag it, but with a delay.


```css
#anchor {
  position: absolute;
  anchor-name: --anchor;
}
#tooltip {
  --w: 12em; /* tooltip width */
  --s: 4em;  /* tail size */
  
  position: absolute;
  width: var(--w);
  bottom: anchor(outside --anchor);
  left: clamp(0px,anchor(center --anchor) - var(--w)/2,100% - var(--w));
  margin-bottom: 1.5em;
  anchor-name: --tooltip;
  position-try: flip-block;
  transition: .3s .5s;
}
```

<p class="codepen" data-height="700" data-pen-title="The Lazy Tooltip Follower" data-preview="true" data-default-tab="result" data-slug-hash="QwGLJLo" data-user="t_afif" style="height: 700px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/QwGLJLo">
  The Lazy Tooltip Follower</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Another version with a boncy effect using `linear()`


<p class="codepen" data-height="700" data-pen-title="The Lazy Tooltip Follower (with a bouncy effect)" data-preview="true" data-default-tab="result" data-slug-hash="myOydgG" data-user="t_afif" style="height: 700px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/myOydgG">
  The Lazy Tooltip Follower (with a bouncy effect)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>