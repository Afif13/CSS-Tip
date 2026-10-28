---
layout: layouts/post.njk
title: Confetti Shape Explosion using random()
description: We all like confetti, right? A fancy demo powered by modern CSS features
date: 2026-10-28
tags: posts
---

Do you want a cool hover effect? Using `random()` and modern features, you can explode any border-only shape into confetti!


{% image "./image.png", "CSS-only confetti shape" %}


```html
<div class="shape"> 
  <i></i> <i></i> <i></i> <i></i> 
  <!-- the more <i>, the more confetti! -->
</div>
```

```css
@property --i {syntax: "<integer>";initial-value: 0;inherits: true}
@property --n {syntax: "<integer>";initial-value: 0;inherits: true}

.shape {
  --d: 18px; /* control the explosion distance */
  --s: shape(...); /* it can be polygon() or any shape function */
  
  position: relative;
}
.shape i {
  --i: sibling-index();
  --n: sibling-count();
}
.shape i:before,
.shape i:after {
  content: "";
  position: absolute;
  height: 5px; /* this controls the thickness */
  aspect-ratio: 1.75;
  background: color-mix(in hsl,#ef476f random(0%,100%),#ade8f4);
  translate: random(-1*var(--d),var(--d)) random(-1*var(--d),var(--d));
  offset:  var(--s) calc(var(--i)*100%/var(--n));
  transition: .3s;
}
.shape:not(:hover) {
  --d: 0px;
}
.shape:not(:hover) i:before,
.shape:not(:hover) i:after {
  background: #ef476f;
}
```

⚠️ Chromium-only for now ⚠️

<p class="codepen" data-theme-id="39604" data-height="450" data-pen-title="Confetti Shape explosion (hover to explode!)" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="Wbpggmy" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a18192-1c8d-74f0-bee3-a7d27b201a43">
  Confetti Shape explosion (hover to explode!)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Want to apply this to an SVG shape? Use [my online converter](https://css-generators.com/svg-to-css/) to get the `shape()` code, then update the `--s` variable and the `aspect-ratio`.


Example with the CodePen and CSS Tricks logos

<p class="codepen" data-theme-id="39604" data-height="450" data-pen-title="Codepen and CSS Tricks confetti explosion!" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="vExzVEm" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a181b3-4c14-7bd8-a257-bcbf44c87ce2">
  Codepen and CSS Tricks confetti explosion!</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>


