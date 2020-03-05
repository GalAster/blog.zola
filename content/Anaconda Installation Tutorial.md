+++
title = "Anaconda 安装教程"
date = 2018-02-23
[taxonomies]
tags = ["python", "anaconda"]
categories = ["Tutorial"]
+++

<h2>安装 Anaconda</h2><p>到清华镜像站下载最新 Anaconda 安装包, Date 倒序排列即可.</p><p>https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/</p><p>然后全局安装, 第二个最新 Python 勾上</p><h2>配置 Anaconda</h2>

```sh
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
conda create -n py2 python=2.7
conda create -n py3 python=3.6```

<p>接下来就没bash什么事了, 切换到新搞的python3环境, 然后我看看, jupyterlab,spyder和vscode走起,其他不要了.</p><p>打开 spyder 开干!</p>

<!-- more -->

<h2>应用</h2><h3>conda</h3><h3>bash 环境命令</h3><p>切换环境</p>

```sh
source activate python3
source deactivate```

<p>安装依赖, 可以叠加多个包名</p>

```sh
conda install tensorflow word2vec numpy --yes```

<p>当分享代码的时候，同时也需要将运行环境分享给大家，执行如下命令可以将当前环境下的 package 信息存入名为 environment 的 YAML 文件中。</p><p><code>conda env export > environment.yaml</code></p><p>同样，当执行他人的代码时，也需要配置相应的环境。这时你可以用对方分享的 YAML 文件来创建一摸一样的运行环境。</p><p><code>conda env create -f environment.yaml</code></p>
