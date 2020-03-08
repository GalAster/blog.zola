+++
title = "英语中的有趣现象"
date = 2019-10-19
[taxonomies]
tags = ["english", "mathematica"]
categories = ["Linguistics"]
+++

<h3>有哪些英语单词倒过来是另一个单词？</h3><pre style="background-color:#2b303b;">
<span style="color:#eb6772;">DictionaryLookup</span><span style="color:#abb2bf;">[</span><span style="color:#eb6772;">x__ </span><span style="color:#adb7c9;">/; </span><span style="color:#eb6772;">DictionaryWordQ</span><span style="color:#adb7c9;">@</span><span style="color:#eb6772;">StringReverse</span><span style="color:#adb7c9;">@</span><span style="color:#eb6772;">x</span><span style="color:#abb2bf;">]</span></pre>
<h3>有哪些英语单词是回文的？</h3><pre style="background-color:#2b303b;">
<span style="color:#eb6772;">DictionaryLookup</span><span style="color:#abb2bf;">[</span><span style="color:#eb6772;">x__ </span><span style="color:#adb7c9;">/; </span><span style="color:#eb6772;">x </span><span style="color:#adb7c9;">=== </span><span style="color:#eb6772;">StringReverse</span><span style="color:#adb7c9;">@</span><span style="color:#eb6772;">x</span><span style="color:#abb2bf;">]</span></pre>
<p>有个慢一点的方法, 但是可以短一点</p><pre style="background-color:#2b303b;">
<span style="color:#eb6772;">DictionaryLookup</span><span style="color:#abb2bf;">[</span><span style="color:#eb6772;">x__ </span><span style="color:#adb7c9;">/; </span><span style="color:#eb6772;">PalindromeQ</span><span style="color:#adb7c9;">@</span><span style="color:#eb6772;">x</span><span style="color:#abb2bf;">]</span></pre>
<h3>哪两个字母不可能连在一起？</h3><p><a href="href=\"https://www.zhihu.com/question/25908268\"">https://www.zhihu.com/question/25908268</a></p><h3>英文各字母使用频率？</h3><p><a href="href=\"https://www.zhihu.com/question/23111432\"">https://www.zhihu.com/question/23111432</a></p><h3>英语单词 26 个首字母出现概率各是多少？</h3><p><a href="href=\"https://www.zhihu.com/question/30077599\"">https://www.zhihu.com/question/30077599</a></p><h2>英语单词哪个字母出现频率最高?</h2><p><a href="href=\"https://www.zhihu.com/question/19805834/answer/67555450\"">https://www.zhihu.com/question/19805834/answer/67555450</a></p>
