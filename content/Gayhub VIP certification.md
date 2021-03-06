+++
title = "Gayhub 加V认证"
date = 2017-11-11
[taxonomies]
tags = ["github"]
categories = ["Tutorial"]
+++

<p>任何社交网站都有大V, 那全球最大的同性交友网站自然也有咯.</p><p>大V当然要有独特的标记, Gayhub的标记是什么样的呢?</p><img src="https://i.loli.net/2018/03/07/5a9fab23d67a8.png"><h2>Warning!!!</h2><p>首先警告一下这个东西超级麻烦, 以后每次提交都要输入 commit 密码</p><p>这还没完, 而且如果你使用 IDE 麻烦会平方.</p><p>另外这个无法补签... 你全绿漏一天你明年再接再厉吧...</p><p>Rebase 之后还丢失认证, 除非使用专用的变基技巧...</p><p>如果你确定你不怕麻烦就是要加V的话那我们开始吧!</p>

<!-- more -->

<h3>应用场景</h3><p>使用这个东西的原因就是 github 并不强制验证提交</p><p>你可以非法获取关注, 填上大佬的邮箱, 然后commit就会被计入大佬的动态里(feed流), 大佬莫名奇妙就被提交了</p><p>还有, 如果你以贵司CTO身份提交一段bug代码那就好玩了...</p><p>大佬为了表明这是亲自提zhuang交bi才会用这个</p><p>所以某种意义上确实是 Github 大V 认证</p><h2>使用gpg签名</h2><h3>产生key</h3><p><code>gpg --gen-key</code>, git 安装自带这个模块.</p><p>然后他会问你一大堆的问题:</p><pre style="background-color:#2b303b;">
<span style="color:#abb2bf;">Please select what kind of key you want:
</span><span style="color:#abb2bf;">   (1) RSA and RSA (default)
</span><span style="color:#abb2bf;">   (2) DSA and Elgamal
</span><span style="color:#abb2bf;">   (3) DSA (sign only)
</span><span style="color:#abb2bf;">   (4) RSA (sign only)
</span><span style="color:#abb2bf;">Your selection?</span></pre>
<p>你想要那种key?<code>(4)</code></p><p>当然是签名专用的咯, DSA,RSA其实都差不多, 当然有ECC就更好了.</p><pre style="background-color:#2b303b;">
<span style="color:#abb2bf;">RSA keys may be between 1024 and 4096 bits long.
</span><span style="color:#abb2bf;">What keysize do you want? (2048) 4096</span></pre>
<p>你想要多长? <code>(4096)</code></p><p>废话当然越长越好啊...</p><pre style="background-color:#2b303b;">
<span style="color:#abb2bf;">Please specify how long the key should be valid.
</span><span style="color:#abb2bf;">         0 = key does not expire
</span><span style="color:#abb2bf;">      &lt;n&gt;  = key expires in n days
</span><span style="color:#abb2bf;">      &lt;n&gt;w = key expires in n weeks
</span><span style="color:#abb2bf;">      &lt;n&gt;m = key expires in n months
</span><span style="color:#abb2bf;">      &lt;n&gt;y = key expires in n years
</span><span style="color:#abb2bf;">Key is valid for? (0)</span></pre>
<p>Key 的有效期? <code>(0)</code></p><p>永久(我认为), 时限确实是个问题, key生成后不能改也不能随便换, 删掉可能会把以前的认证某些情况下会掉.</p><p>然后输入自己的github的用户名和联系邮箱, 可以带一条 commit.</p><pre style="background-color:#2b303b;">
<span style="color:#abb2bf;">GalAster
</span><span style="color:#abb2bf;">galaster@foxmail.com
</span><span style="color:#abb2bf;">From 2018-2-22-18:24</span></pre>
<p>然后需要一个 commit 密码, 输入是看不见的, 要输两遍防止输错</p><p><b>以后每次commit都要输入这个密码!</b></p><h3>启用key</h3><p>到这里就完成了, 接下来查看你的key列表:</p><p><code>gpg --list-keys</code></p><pre style="background-color:#2b303b;">
<span style="color:#eb6772;">/.gnupg/pubring.gpg
</span><span style="color:#eb6772;">---------------------------------
</span><span style="color:#eb6772;">pub</span><span style="color:#abb2bf;">   4096R/9E91A3EF 2018-02-22
</span><span style="color:#eb6772;">uid</span><span style="color:#abb2bf;">                  GalAster (From 2018-2-22-18:24) </span><span style="color:#adb7c9;">&lt;</span><span style="color:#abb2bf;">galaster@foxmail.com</span><span style="color:#adb7c9;">&gt;</span></pre>
<p>这里的 9E91A3EF 就是 key 的编号, 接下来导出秘钥</p><p><code>gpg --armor --export pub 9E91A3EF</code></p><pre style="background-color:#2b303b;">
<span style="color:#abb2bf;">-----BEGIN PGP PUBLIC KEY BLOCK-----
</span><span style="color:#abb2bf;">XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
</span><span style="color:#abb2bf;">-----END PGP PUBLIC KEY BLOCK-----</span></pre>
<p>把以上部分输入github即可: [Github-GPG](https://github.com/settings/gpg/new)</p><p>接下来强制启用commit签名</p><pre style="background-color:#2b303b;">
<span style="color:#eb6772;">git</span><span style="color:#abb2bf;"> config</span><span style="color:#eb6772;"> --global</span><span style="color:#abb2bf;"> commit.gpgsign true
</span><span style="color:#eb6772;">git</span><span style="color:#abb2bf;"> config</span><span style="color:#eb6772;"> --global</span><span style="color:#abb2bf;"> user.signingkey 9E91A3EF
</span><span style="color:#eb6772;">git</span><span style="color:#abb2bf;"> config</span><span style="color:#eb6772;"> --global</span><span style="color:#abb2bf;"> alias.commit commit</span><span style="color:#eb6772;"> -S</span></pre>
<p>如果某个项目不要签名, 那就单独取消</p><pre style="background-color:#2b303b;">
<span style="color:#eb6772;">git</span><span style="color:#abb2bf;"> config commit.gpgsign false</span></pre>
<h2>IDE 配置</h2><p>Well, 如果你使用IDE就超麻烦了, 如果你使用 Win 那就 <span class="math">$\displaystyle{\small{麻烦×2, 麻烦^2, 麻烦^{麻烦^{麻烦^\cdots}}}}$</span>  了...</p><p>我看了好多 Linux 的教程, 外加一个 Mac 唯独没有 win 的...</p><p>看了两个小时原理才摸索出一个方法来...</p><h3>Win 用户</h3><p>我把这个问题里的一大串过程看了一遍</p><p>[Stackoverflow: GPG in Intellij](https://stackoverflow.com/questions/46863981/how-to-sign-git-commits-from-within-an-ide-like-intellij)</p><p>首先需要把 <code>tty</code> 关掉, 输入<code>echo 'no-tty' >> ~/.gnupg/gpg.conf</code>.</p><p>tty 大概就是终端(teletypewriter)模式的意思, IDE里的那叫Termial乃至Console, 和tty不是一回事, 我本来也没弄明白, 绕了半天.</p><p>其次需要一个 <code>gpg-agent</code> 来代替 <code>tty</code>, 这个可以由某种加密软件来充当, 这我只知道putty自带的那个可以, 然后捣鼓了半天还是拎不清由谁来代理加密.</p><p>唉, 看看有没有别的软件...</p><p>我又搜了搜 gpg+win 找到一个 [Gpg4win](https://gpg4win.org/get-gpg4win.html) 这名字... 那就它了!</p><p>下载速度很慢...天生慢, 因为挂代理都没用...</p><p>毕竟win用户从来没有加密需求>>逃</p><p>安装, 然后git指向这个可执行文件(shell下要转义, powershell下就算了)</p><pre style="background-color:#2b303b;">
<span style="color:#abb2bf;">git config --global gpg.program &quot;C:\\Program Files (x86)\\GnuPG\\bin\\gpg.exe&quot;</span></pre>
<p>还没完, 打开那个 Kleopatra 软件, 导入你的秘钥.</p><p>然后你可以去你的 IDE 里点 push 了, 每次commit都要输密码了.</p><p>如果你还是有问题, 那么可以手动更改全局设定</p><img src="https://i.loli.net/2018/03/07/5a9fae742cce1.png"><h3>Linux 用户</h3><p>虽然 Linux 动手能力很强, 但是这个还是不太好找的</p><p>解决方案: <a href="href=\"https://youtrack.jetbrains.com/oauth?state=%2Fissue%2FIDEA-127802\"">Jetbrains: GPG in Linux</a></p><p><code>git config --global gpg.program /usr/local/bin/gpg</code></p><p>然后新建一个bash脚本放在 <code>/usr/local/bin/gpg</code></p><pre style="background-color:#2b303b;">
<span style="font-style:italic;color:#5f697a;">#!/bin/bash
</span><span style="color:#eb6772;">/usr/bin/gpg --batch --no-tty </span><span style="color:#9acc76;">&quot;$</span><span style="color:#eb6772;">@</span><span style="color:#9acc76;">&quot;</span></pre>
<h3>Mac 用户</h3><p>本来对 Mac 用户要收费的, 但我干掉了这个难题心情不错, 附赠的...</p><p>解决方案: <a href="href=\"https://stackoverflow.com/questions/39494631/gpg-failed-to-sign-the-data-fatal-failed-to-write-commit-object-git-2-10-0\"">Stackoverflow: GPG on Mac</a></p><pre style="background-color:#2b303b;">
<span style="color:#eb6772;">brew</span><span style="color:#abb2bf;"> install pinentry-mac
</span><span style="color:#5ebfcc;">echo </span><span style="color:#9acc76;">&quot;no-tty&quot; </span><span style="color:#adb7c9;">&gt;&gt; </span><span style="color:#eb6772;">~</span><span style="color:#abb2bf;">/.gnupg/gpg.conf
</span><span style="color:#5ebfcc;">echo </span><span style="color:#abb2bf;">$(</span><span style="color:#eb6772;">which</span><span style="color:#abb2bf;"> pinentry-mac) </span><span style="color:#adb7c9;">&gt;&gt; </span><span style="color:#eb6772;">~</span><span style="color:#abb2bf;">/.gnupg/gpg-agent.conf</span></pre>
