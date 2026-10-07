---
layout: layouts/post.njk
title: Random Wavy Dividers
description: Combining shape() and random() to create fancy wavy dividers
date: 2026-10-07
tags: posts
---

After the [blob shapes](/random-blob/), here is another shape we can build using `random()` to create a unique user experience. A fancy wavy divider!

{% image "./image.png", "CSS-only wavy divider" %}

```css
.wavy {
  --n: 13;   /* if you change this, you need to add more points .. we don't have loops in CSS */
  --d: 60px; /* control the depth, can be percentage */
  
  --_r: element-scoped,0px,var(--d);
  --x0: (50%/var(--n) + 000%/var(--n));
  --y0: (100% - random(--0 var(--_r)));
  --x1: (50%/var(--n) + 100%/var(--n));
  --y1: (100% - random(--1 var(--_r)));
  --x2: (50%/var(--n) + 200%/var(--n));
  --y2: (100% - random(--2 var(--_r)));
  --x3: (50%/var(--n) + 300%/var(--n));
  --y3: (100% - random(--3 var(--_r)));
  --x4: (50%/var(--n) + 400%/var(--n));
  --y4: (100% - random(--4 var(--_r)));
  /* etc ... */

  clip-path: shape(from 100% 100%,vline to 0,hline to 0,vline to 100%,
    curve  to calc((var(--x1 ) + var(--x2 ))/2) calc((var(--y1 ) + var(--y2 ))/2) with calc(var(--x1)) calc(var(--y1)),
    smooth to calc((var(--x2 ) + var(--x3 ))/2) calc((var(--y2 ) + var(--y3 ))/2),
    smooth to calc((var(--x3 ) + var(--x4 ))/2) calc((var(--y3 ) + var(--y4 ))/2),
    smooth to calc((var(--x4 ) + var(--x5 ))/2) calc((var(--y4 ) + var(--y5 ))/2),
    /* etc ... */
    smooth to 100% 100%,
  );
}
```

⚠️ Chromium-only for now ⚠️

<p class="codepen" data-theme-id="39604" data-height="450" data-pen-title="Top random wavy divider" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="PwpOrjy" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a115c0-9c57-7f47-9c30-09bd68b63725">
  Top random wavy divider</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


We can adjust the code to have the wave on the top:

```css
.wavy {
  --n: 13;   /* if you change this, you need to add more points .. we don't have loops in CSS */
  --d: 60px; /* control the depth, can be percentage */
  
  --_r: element-scoped,0px,var(--d);
  --x0: (50%/var(--n) + 000%/var(--n));
  --y0: (random(--0 var(--_r)));
  --x1: (50%/var(--n) + 100%/var(--n));
  --y1: (random(--1 var(--_r)));
  --x2: (50%/var(--n) + 200%/var(--n));
  --y2: (random(--2 var(--_r)));
  --x3: (50%/var(--n) + 300%/var(--n));
  --y3: (random(--3 var(--_r)));
  --x4: (50%/var(--n) + 400%/var(--n));
  --y4: (random(--4 var(--_r)));
  /* etc ... */

  clip-path: shape(from 100% 0,vline to 100%,hline to 0,vline to 0,
    curve  to calc((var(--x1 ) + var(--x2 ))/2) calc((var(--y1 ) + var(--y2 ))/2) with calc(var(--x1)) calc(var(--y1)),
    smooth to calc((var(--x2 ) + var(--x3 ))/2) calc((var(--y2 ) + var(--y3 ))/2),
    smooth to calc((var(--x3 ) + var(--x4 ))/2) calc((var(--y3 ) + var(--y4 ))/2),
    smooth to calc((var(--x4 ) + var(--x5 ))/2) calc((var(--y4 ) + var(--y5 ))/2),
    /* etc ... */
    smooth to 100% 0,
  );
}
```

<p class="codepen" data-theme-id="39604" data-height="450" data-pen-title="Top random wavy divider" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="vExWqpj" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a115c6-2235-71a3-bc94-f3382c71065e">
  Top random wavy divider</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


Or both top and bottom:

<p class="codepen" data-theme-id="39604" data-height="500" data-pen-title="Random wavy divider" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="zxZPVJZ" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a115cc-0cbc-790a-b289-3aec51ca76dd">
  Random wavy divider</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Until better support, you can use my online generator to get a static version: [css-generators.com/wavy-divider](https://css-generators.com/wavy-divider/)