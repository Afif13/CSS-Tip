---
layout: layouts/post.njk
title: Alignment in Anchor Positioning using position-area
description: An interactive demo to understand how to control the alignment using the position-area property
date: 2025-10-15
tags: posts
---

The `position-area` property allows you to control the placement of an absolutely positioned element relative to its anchor box. It considers a 3x3 grid defined by the **containing block** of the absolutely positioned element and the **edges** of the anchor box.

```css
.anchor {
  anchor-name: --a;
}
.element {
  position: absolute;
  position-anchor: --a;
}
```

{% image "./image.png", "Overview of the position-area grid" %}

You can select an area that consists of one or more adjacent cells of the grid. That area becomes the **new containing block** of the absolutely positioned element where it's aligned.

Here is an interactive demo where you can select an area from among all 36 possibilities and get its code. You can also drag the anchor element and see how the grid behaves.

<style>
  .demo {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    min-height: 600px;
    margin-block: 2em;
  }
  .demo form {
    width: 250px;
    flex-grow: 1;
    padding-right: 10px;
    contain: size;
    overflow: auto;
    min-height: 220px;
  }
  .demo form p {
    margin: .5em 0;
  }
  .demo .result {
    flex-grow: 1;
    width: 500px;
    min-height: 500px;
    display: grid;
    grid-template-rows: 1fr auto;
  }
  .demo .container {
    position: relative;
    border: 3px dashed;
  }
  .demo .container .anchor {
    position: absolute;
    anchor-name: --a;
    left: 50%;
    top: 30%;
    background: #ddd;
    padding: .5rem;
    user-select: none;
    font-size: 3em;
    cursor: move;
  }
  .demo .container .box {
    position: absolute;
    position-anchor: --a;
    padding: .5em;
    font-weight: bold;
    place-self: stretch;
    background: lightblue;
    opacity: .8;
    pointer-events: none;
  }
  .demo .container l:before {
    content: "";
    position: absolute;
    inset-block: min(0px,anchor(--a start)) min(0px,anchor(--a end));
    inset-inline: anchor(--a start) anchor(--a end);
    border-inline: 2px dashed #f92672;
    pointer-events: none;
  }
  .demo .container l:after {
    content: "";
    position: absolute;
    inset-inline: min(0px,anchor(--a start)) min(0px,anchor(--a end));
    inset-block: anchor(--a start) anchor(--a end);
    border-block: 2px dashed #f92672;
    pointer-events: none;
  }
  .demo pre[class*=language-] {
    margin: .5em 0;
    padding: .5em;
  }
  form p {
    font-weight: bold;
  }
  .demo label {
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 5px;
    font-weight: 600;
  }
  select {
    font: inherit;
  }
  .demo input {
    width: 20px;
    aspect-ratio: 1;
    cursor: pointer;
    margin: 0;
  }
  form label:after {
    content: "";
    width: 46px;
    aspect-ratio: 1;
    border: 1px solid;
    --c:,conic-gradient(lightblue 0 0) no-repeat;
    background: 
     conic-gradient(from 90deg at 1px 1px,#0000 25%,#000 0) -1px -1px/calc((100% + 2px)/3) calc((100% + 2px)/3)
     var(--b,);
  }
  form .one,
  form .two {
    display: flex;
    flex-wrap: wrap;
    gap: 15px 10px;
  }
  :nth-child(1 of .one) label:nth-child(1):after {--b:var(--c) 0    0/16px 16px}
  :nth-child(1 of .one) label:nth-child(2):after {--b:var(--c) 50%  0/16px 16px}
  :nth-child(1 of .one) label:nth-child(3):after {--b:var(--c) 100% 0/16px 16px}
  :nth-child(1 of .one) label:nth-child(4):after {--b:var(--c) 0 50% /16px 16px}
  :nth-child(1 of .one) label:nth-child(5):after {--b:var(--c) 50%   /16px 16px}
  :nth-child(1 of .one) label:nth-child(6):after {--b:var(--c) 100% 50%/16px 16px}
  :nth-child(1 of .one) label:nth-child(7):after {--b:var(--c) 0 100%/16px 16px}
  :nth-child(1 of .one) label:nth-child(8):after {--b:var(--c) 50% 100%/16px 16px}
  :nth-child(1 of .one) label:nth-child(9):after {--b:var(--c) 100% 100%/16px 16px}

  :nth-child(2 of .one) label:nth-child(1):after {--b:var(--c) 0    0/32px 16px}
  :nth-child(2 of .one) label:nth-child(2):after {--b:var(--c) 0  50%/32px 16px}
  :nth-child(2 of .one) label:nth-child(3):after {--b:var(--c) 0 100%/32px 16px}
  :nth-child(2 of .one) label:nth-child(4):after {--b:var(--c) 100% 0/32px 16px}
  :nth-child(2 of .one) label:nth-child(5):after {--b:var(--c) 100% 50%/32px 16px}
  :nth-child(2 of .one) label:nth-child(6):after {--b:var(--c) 100% 100%/32px 16px}
  :nth-child(2 of .one) label:nth-child(7):after {--b:var(--c) 0 0/16px 32px}
  :nth-child(2 of .one) label:nth-child(8):after {--b:var(--c) 50% 0/16px 32px}
  :nth-child(2 of .one) label:nth-child(9):after {--b:var(--c) 100% 0/16px 32px}
  :nth-child(2 of .one) label:nth-child(10):after {--b:var(--c) 0 100%/16px 32px}
  :nth-child(2 of .one) label:nth-child(11):after {--b:var(--c) 50% 100%/16px 32px}
  :nth-child(2 of .one) label:nth-child(12):after {--b:var(--c) 100% 100%/16px 32px}

  :nth-child(3 of .one) label:nth-child(1):after {--b:var(--c) 0 0/48px 16px}
  :nth-child(3 of .one) label:nth-child(2):after {--b:var(--c) 50%/48px 16px}
  :nth-child(3 of .one) label:nth-child(3):after {--b:var(--c) 0 100%/48px 16px}
  :nth-child(3 of .one) label:nth-child(4):after {--b:var(--c) 0/16px 48px}
  :nth-child(3 of .one) label:nth-child(5):after {--b:var(--c) 50%/16px 48px}
  :nth-child(3 of .one) label:nth-child(6):after {--b:var(--c) 100%/16px 48px}

  :nth-child(1 of .two) label:nth-child(1):after {--b:var(--c) 0 0/32px 32px}
  :nth-child(1 of .two) label:nth-child(2):after {--b:var(--c) 100% 0/32px 32px}
  :nth-child(1 of .two) label:nth-child(3):after {--b:var(--c) 0 100%/32px 32px}
  :nth-child(1 of .two) label:nth-child(4):after {--b:var(--c) 100% 100%/32px 32px}

  :nth-child(2 of .two) label:nth-child(1):after {--b:var(--c) 0 0/100% 32px}
  :nth-child(2 of .two) label:nth-child(2):after {--b:var(--c) 100% 100%/100% 32px}
  :nth-child(2 of .two) label:nth-child(3):after {--b:var(--c) 0/32px 100%}
  :nth-child(2 of .two) label:nth-child(4):after {--b:var(--c) 100%/32px 100%}

  :nth-child(4 of .one) label:nth-child(1):after {--b:var(--c) 0/100% 100%}
</style>
<div class=demo>
  <form>
    <p>1 Cell</p>
    <div class="one">
      <label><input type="radio" name="area" value="top left" checked></label>
      <label><input type="radio" name="area" value="top center"></label>
      <label><input type="radio" name="area" value="top right"></label>
      <label><input type="radio" name="area" value="center left"></label>
      <label><input type="radio" name="area" value="center"></label>
      <label><input type="radio" name="area" value="center right"></label>
      <label><input type="radio" name="area" value="bottom left"></label>
      <label><input type="radio" name="area" value="bottom center"></label>
      <label><input type="radio" name="area" value="bottom right"></label>
    </div>
    <p>2 Cells</p>
    <div class="one">
      <label><input type="radio" name="area" value="top span-left"></label>
      <label><input type="radio" name="area" value="center span-left"></label>
      <label><input type="radio" name="area" value="bottom span-left"></label>
      <label><input type="radio" name="area" value="top span-right"></label>
      <label><input type="radio" name="area" value="center span-right"></label>
      <label><input type="radio" name="area" value="bottom span-right"></label>
      <label><input type="radio" name="area" value="span-top left"></label>
      <label><input type="radio" name="area" value="span-top center"></label>
      <label><input type="radio" name="area" value="span-top right"></label>
      <label><input type="radio" name="area" value="span-bottom left"></label>
      <label><input type="radio" name="area" value="span-bottom center"></label>
      <label><input type="radio" name="area" value="span-bottom right"></label>
    </div>
    <p>3 Cells</p>
    <div class="one">
      <label><input type="radio" name="area" value="top"></label>
      <label><input type="radio" name="area" value="center span-all"></label>
      <label><input type="radio" name="area" value="bottom"></label>
      <label><input type="radio" name="area" value="left"></label>
      <label><input type="radio" name="area" value="span-all center"></label>
      <label><input type="radio" name="area" value="right"></label>
    </div>
    <p>4 Cells</p>
    <div class="two">
      <label><input type="radio" name="area" value="span-top span-left"></label>
      <label><input type="radio" name="area" value="span-top span-right"></label>
      <label><input type="radio" name="area" value="span-bottom span-left"></label>
      <label><input type="radio" name="area" value="span-bottom span-right"></label>
    </div>
    <p>6 Cells</p>
    <div class="two">
      <label><input type="radio" name="area" value="span-top"></label>
      <label><input type="radio" name="area" value="span-bottom"></label>
      <label><input type="radio" name="area" value="span-left"></label>
      <label><input type="radio" name="area" value="span-right"></label>
    </div>
    <p>9 Cells</p>
    <div class="one">
      <label><input type="radio" name="area" value="span-all"></label>
    </div>
  </form>
  <div class="result">
    <div class="container">
      <div class="anchor">⚓️</div>
      <div class="box" style="position-area: top left;place-self: stretch;">CSS Is Awesome</div>
      <l></l>
    </div>
    <pre class="language-css" tabindex="0"><code class="language-css"><span class="token selector">.element</span> <span class="token punctuation">{</span>
  <span class="token property">position-area</span><span class="token punctuation">:</span> <span class="selected-value">top left</span><span class="token punctuation">;</span>
  <span class="token property">justify-self</span><span class="token punctuation">:</span> <select data-element=".box" data-property="justify-self"><option value="normal">normal</option><option value="anchor-center">anchor-center</option><option value="stretch" selected>stretch</option><option value="start">start</option><option value="center">center</option><option value="end">end</option></select><span class="token punctuation">;</span>
  <span class="token property">align-self</span><span class="token punctuation">:</span> <select data-element=".box" data-property="align-self"><option value="normal">normal</option><option value="anchor-center">anchor-center</option><option value="stretch" selected>stretch</option><option value="start">start</option><option value="center">center</option><option value="end">end</option></select><span class="token punctuation">;</span>
<span class="token punctuation">}</span></code></pre>
    <label><input type="checkbox" name="logical"> Switch to logical values</label>
  </div>
</div>

<script>
const anchor = document.querySelector('.demo .anchor');
const c = document.querySelector('.demo .container');
let isDragging = false;
let offsetX, offsetY;

anchor.addEventListener('mousedown', (e) => {
  isDragging = true; 
  const rect = anchor.getBoundingClientRect();
  offsetX = e.clientX - rect.left;
  offsetY = e.clientY - rect.top;
  
  anchor.style.cursor = 'grabbing';
});

document.addEventListener('mousemove', (e) => {
  if (!isDragging) return;
  
  const r = c.getBoundingClientRect();
  anchor.style.left = (e.clientX - offsetX - r.left) + 'px';
  anchor.style.top = (e.clientY - offsetY - r.top) + 'px';
});

document.addEventListener('mouseup', () => {
  isDragging = false;
  anchor.style.cursor = 'move';
});

document.querySelector('form').addEventListener('input', function() {
  let val = document.querySelector('[name="area"]:checked').value;
  let log = document.querySelector('[name="logical"]').checked;

  if(log) {
    if(val == "top")
      val = "block-start";
    if(val == "bottom")
      val = "block-end";
    if(val == "left")
      val = "inline-start";
    if(val == "right")
      val = "inline-end";

    if(val == "span-top")
      val = "span-y-start";
    if(val == "span-bottom")
      val = "span-y-end";
    if(val == "span-left")
      val = "span-x-start";
    if(val == "span-right")
      val = "span-x-end";
    val = val.replace("top","start").replace("left","start").replace("bottom","end").replace("right","end");
    if(val == "start start")
      val = "start";
    if(val == "end end")
      val = "end";
    if(val == "span-start span-start")
      val = "span-start";
    if(val == "span-end span-end")
      val = "span-end";
  }

  document.querySelector('.demo .box').style.positionArea = val;
  document.querySelector('.demo .selected-value').innerHTML = val;
});

document.querySelector('[name="logical"]').addEventListener('change', function() {
  document.querySelector('form').dispatchEvent(new Event('input'));
});

let all_select = document.querySelectorAll(".demo select");

for (let i=0;i<all_select.length;i++) {
  all_select[i].addEventListener("change", function(e) {
    e.target.closest(".demo").querySelector(e.target.dataset.element).style.setProperty(e.target.dataset.property,e.target.value)
  })
}

</script>

I am using a stretch alignment to illustrate the different areas, but you can change it to place the element wherever you want within the selected area. 

The `normal` value is the default value and has an interesting behavior. It places the element as close as possible to the anchor, which is what you will want in 90% of cases, so you will rarely need to update the alignment.

The `anchor-center` is a special value different from `center`. `center` considers the center of the selected area, while `anchor-center` considers the center of the anchor in the relevant axis. 

{% image "./image2.png", "Center vs anchor-center" %}

`anchor-center` is a [safe alignment value](/safe-align/). If centering is not possible, the element will shift to remain within the selected area. 

More details about alignment: [The Fundamentals of CSS Alignment](/explore/alignment/)