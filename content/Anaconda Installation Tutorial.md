+++
title = "Anaconda 安装教程"
date = 2018-02-23
[taxonomies]
tags = ["python", "anaconda"]
categories = ["Tutorial"]
+++

<h2>安装 Anaconda</h2><p>到清华镜像站下载最新 Anaconda 安装包, Date 倒序排列即可.</p><p><a href="href=\"https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/\"">https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/</a></p><p>然后全局安装, 第二个最新 Python 勾上</p><h2>配置 Anaconda</h2><pre style="background-color:#2b303b;">
<span style="color:#eb6772;">conda</span><span style="color:#abb2bf;"> config</span><span style="color:#eb6772;"> --add</span><span style="color:#abb2bf;"> channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
</span><span style="color:#eb6772;">conda</span><span style="color:#abb2bf;"> config</span><span style="color:#eb6772;"> --add</span><span style="color:#abb2bf;"> channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
</span><span style="color:#eb6772;">conda</span><span style="color:#abb2bf;"> config</span><span style="color:#eb6772;"> --set</span><span style="color:#abb2bf;"> show_channel_urls yes
</span><span style="color:#eb6772;">conda</span><span style="color:#abb2bf;"> create</span><span style="color:#eb6772;"> -n</span><span style="color:#abb2bf;"> py2 python=2.7
</span><span style="color:#eb6772;">conda</span><span style="color:#abb2bf;"> create</span><span style="color:#eb6772;"> -n</span><span style="color:#abb2bf;"> py3 python=3.6</span></pre>
<p>接下来就没 bash 什么事了, 切换到新搞的 python3 环境, 然后我看看, jupyterlab, spyder 和 vscode 走起, 其他不要了.</p><p>打开 spyder 开干!</p>

<!-- more -->

<h2>应用</h2><h3>conda</h3><h3>bash 环境命令</h3><p>切换环境</p><pre style="background-color:#2b303b;">
<span style="color:#5ebfcc;">source</span><span style="color:#abb2bf;"> activate python3
</span><span style="color:#5ebfcc;">source</span><span style="color:#abb2bf;"> deactivate</span></pre>
<p>安装依赖, 可以叠加多个包名</p><pre style="background-color:#2b303b;">
<span style="color:#eb6772;">conda</span><span style="color:#abb2bf;"> install tensorflow word2vec numpy</span><span style="color:#eb6772;"> --yes</span></pre>
<p>当分享代码的时候，同时也需要将运行环境分享给大家，执行如下命令可以将当前环境下的 package 信息存入名为 environment 的 YAML 文件中。</p><p><code>conda env export > environment.yaml</code></p><p>同样，当执行他人的代码时，也需要配置相应的环境。这时你可以用对方分享的 YAML 文件来创建一摸一样的运行环境。</p><p><code>conda env create -f environment.yaml</code></p>
