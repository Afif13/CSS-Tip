---
layout: layouts/post.njk
title: Recreating the <filedset> component and its <legend>
description: Using basic HTML and a few lines of CSS to recreate the fieldset component
date: 2026-01-21
tags: posts
---

Using a minimal HTML code and modern CSS to recreate the [`<fieldset>` component](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/fieldset). A responsive implementation easy to control using CSS variables. It's also direction-aware with real transparency!

{% image "./image.png", "CSS-only filedset component" %}

```html
<div class="fieldset">
  <h3>The Legend</h3>
  <!-- place your content here  -->
</div>
```

```css
.fieldset {
  --r: 20px; /* radius of the box */
  --p: 1em;  /* padding of the box */
  --b: 6px;  /* border thickness */
  --g: 12px; /* gap between the legend and border */
  --o: 10px; /* to offset the legend from the side */
  --c: #db3a34;
  
  padding: var(--p);
  position: relative;
  z-index: 0;
  display: flow-root; /* to avoid margin collapsing */
}
.fieldset h3 {
  margin: 
    calc(var(--b)/2 - .5lh - var(--p)) 
    calc(var(--r) - var(--p)) 
    calc(var(--p) - .5lh - var(--b)/2);
  display: flex;
  gap: var(--g);
}
.fieldset h3:before,
.fieldset h3:after {
  content: "";
  height: var(--b);
  background: var(--c);
  width: var(--o);
  margin-top: calc(.5lh - var(--b)/2)
}
.fieldset h3:after {
  flex: 1;
}
.fieldset:before {
  content:"";
  position: absolute;
  z-index: -1;
  inset: 0;
  border-radius: var(--r);
  border: var(--b) solid var(--c);
  clip-path: polygon(0 0,var(--r) 0,var(--r) 50%,calc(100% - var(--r)) 50%, calc(100% - var(--r)) 0,100% 0,100% 100%,0 100%);
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="EayXyby" data-pen-title="Recreating &amp;lt;fieldset&amp;gt; (and &amp;lt;legend&amp;gt;) using CSS" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/EayXyby">
  Recreating &lt;fieldset&gt; (and &lt;legend&gt;) using CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>