---
layout: layouts/post.njk
title: Trim extra space using text-box
description: An interactive tool to illustrate how to trim the extra space below and above text
date: 2025-02-26
tags: posts
---

<style>
  select {
    font-size: 1em;
    margin-block: .1em;
  }
  section {
    border: 1px solid;
    margin: 10px auto;
    font-size: 1.5em;
    line-height: 1.5;
    max-width: 400px;
  }
  section > * {
    margin: 0;
  }
  .trim {
    text-align: center;
    font-size: min(61px,12vw);
    font-weight: bold;
    line-height: 2.5;
    border-block: 1px solid #f92672;
    position: relative;
    overflow: hidden;
    margin-block: .5em;
  }
  p.trim:before {
    content: "";
    position: absolute;
    inset: 3px auto 4px 40px;
    width: 10px;
    background: #f92672;
    clip-path: polygon(50% 0,100% 10px,65% 10px,65% calc(100% - 10px),100% calc(100% - 10px),50% 100%,0 calc(100% - 10px),35% calc(100% - 10px),35% 10px,0 10px);
  }
  p.trim::after {
    content: "Line height";
    position: absolute;
    font-size: 20px;
    font-weight: 400;
    inset: 0 auto 0 40px;
    line-height: 1;
    rotate: -90deg;
    color: #f92672;
  }
  .trim span {
    position: relative;
    display: inline-block;
    white-space: nowrap;
    justify-self: center;
    background: #69D2E7;
  }
  .trim span:before {
    content: "";
    position: absolute;
    inset: 0;
    box-shadow: 0 0 0 100px #fff5;
    z-index: 1;
    clip-path: inset(-200px 0);
}
  @media (width < 450px) {
    .trim:before,
    .trim:after {
      display: none;
    }
  }
</style>


Ready for the new `text-box` property? With it, you can easily remove extra space above and below your text. Adjust the setting to see the effect of the different values.

⚠️ Support is limited (Chrome-only for now) ⚠️


<form>
From the top <select name="top">
  <option value="0" selected>trim Nothing</option>
  <option value="text">trim to Ascender</option>
  <option value="cap">trim to Uppercase</option>
  <option value="ex">trim to Lowercase</option>
</select> 
and from the bottom <select name="bottom">
  <option value="0" selected>trim Nothing</option>
  <option value="text">trim to Descender</option>
  <option value="alphabetic">trim to Baseline</option>
</select> 
</form>

<p class="trim"><span>Ab-xy-12-Êç</span></p>

```css
.text {
  text-box: auto;
}
```

<section>
  <h3>Block of Text</h3>
  <p>For a multi-line content, we trim the top of the first line and the bottom of the last line (jpq).</p>
</section>



<script>
let code = document.querySelector('pre code');
let trim = document.querySelector('.trim span');
let section = document.querySelector('section');

document.querySelector('form').addEventListener('input', function() {
  let top = document.querySelector("select[name=top]").value;
  let bottom = document.querySelector("select[name=bottom]").value;

  if(top==0 && bottom == 0) {
    code.innerHTML=`<span class="token selector">.text</span> <span class="token punctuation">{</span><br>  <span class="token property">text-box</span><span class="token punctuation">:</span> normal<span class="token punctuation">;</span><br><span class="token punctuation">}</span>`;
    trim.style.textBox= 'normal';
    section.style.textBox= 'normal';
  } else if(top == 0) {
    if(bottom == "text") {
      code.innerHTML=`<span class="token selector">.text</span> <span class="token punctuation">{</span><br>  <span class="token property">text-box</span><span class="token punctuation">:</span> trim-end text<span class="token punctuation">;</span> <br><span class="token punctuation">}</span>`;
    } else {
      code.innerHTML=`<span class="token selector">.text</span> <span class="token punctuation">{</span><br>  <span class="token property">text-box</span><span class="token punctuation">:</span> trim-end text ${bottom}<span class="token punctuation">;</span> <br><span class="token punctuation">}</span>`;
    }
    trim.style.textBox= `trim-end text ${bottom}`;
    section.style.textBox= `trim-end text ${bottom}`;
  } else if(bottom == 0) {
    if(top == "text") {
      code.innerHTML=`<span class="token selector">.text</span> <span class="token punctuation">{</span><br>  <span class="token property">text-box</span><span class="token punctuation">:</span> trim-start text<span class="token punctuation">;</span> <br><span class="token punctuation">}</span>`;

    } else {
      code.innerHTML=`<span class="token selector">.text</span> <span class="token punctuation">{</span><br>  <span class="token property">text-box</span><span class="token punctuation">:</span> trim-start ${top} text<span class="token punctuation">;</span> <br><span class="token punctuation">}</span>`;
    }
    trim.style.textBox= `trim-start ${top} text`;
    section.style.textBox= `trim-start ${top} text`;
  } else if(top == bottom){
    code.innerHTML=`<span class="token selector">.text</span> <span class="token punctuation">{</span><br>  <span class="token property">text-box</span><span class="token punctuation">:</span> ${top}<span class="token punctuation">;</span> <span class="token comment"></span><br><span class="token punctuation">}</span>`;
    trim.style.textBox= `${top}`;
    section.style.textBox= `${top}`;
  } else { 
    code.innerHTML=`<span class="token selector">.text</span> <span class="token punctuation">{</span><br>  <span class="token property">text-box</span><span class="token punctuation">:</span> ${top} ${bottom}<span class="token punctuation">;</span><br><span class="token punctuation">}</span>`;
    trim.style.textBox=`${top} ${bottom}`;
    section.style.textBox=`${top} ${bottom}`;
  }
});
</script>

