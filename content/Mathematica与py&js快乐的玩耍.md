+++
title = "Mathematica与py&js快乐的玩耍"
date = 2020-03-01
[taxonomies]
tags = ["mathematica", "zmq"]
categories = ["Tutorial", "Programming"]
+++

<p>title: 让 mathematica 与 py & js 快乐的玩耍</br></br></br></p><h2>安装 ZeroMQ</h2><h3>Win 用户</h3><p>安装最新的 python, nodejs 以及 git</p><ul><li><p>Python: https://www.python.org/downloads/</p></li></ul><ul><li><p>NodeJS: https://nodejs.org/en/</p></li></ul><ul><li><p>GitGUI: https://git-scm.com/downloads</p></li></ul><p>新建一个 sh 文件 <code>i sec.sh</code> , 里面写</p>

```bash
#!/usr/bin/env bash
conda install pyzmq -yes || python -m pip install zmq
cd ~ && npm install zeromq && mv node_modules .node_modules
echo "Ctrl + C 退出" && sleep 86400```

<p>双击运行即可, 若跳警告, 统统无视即可</p>

<!-- more -->

<p>Win 不手操 <code>%Path%</code> 是没有 <code>pip</code> 的, 只有 <code>python -m pip</code> , 当初我学 python 被这个坑死了...</p><p>安装成功的话运行如下代码应该得到和我类似的结果</p>

```mma
FindExternalEvaluators[][Delete[#, {#, 1, 1}&/@Range@Length@#]&]
py=StartExternalSession["Python"]
js=StartExternalSession["NodeJS"]```

<img src=" https://i.loli.net/2018/02/23/5a8f7fb96e9ea.png"><h3>Linux 用户</h3><p>Linux 用户不用教, 都是大佬, 肯定能自己搞定的!</p><h3>Mac 用户</h3><p>Mac 用户可以出钱请我装. 不知道写两行脚本售价 $99 有没有人买23333.</p><h2>测试</h2><p>嗯, 其实装完 git 就能跑 bash 了.</p>

```mma
Bash[command_String]:=RunProcess[{
"C:\\Program Files\\Git\\bin\\bash.exe",
"-c",
command
}, "StandardOutput"]
Bash["bash --version | head -1 | tr -d '\n'"]```

<img src=" https://i.loli.net/2018/02/23/5a8f7fba3f404.png"><p>就是怎么想怎么蛋疼, 我为什么要在 Mathematica 里用bash...</p><p>等会儿, 还是有点用的, 装个库什么的...</p><p>装个 <code>numpy</code> 用用先</p><img src=" https://i.loli.net/2018/02/23/5a8f94da4d2b8.png"><p>可以看到下面的建议栏跳出来了, 说明数据类型已经自动转化为 Mathematica 支持的类型了, 上面的列表的写法也是Mathematica的列表写法.</p><p>试了下图片和函数都不能导出...那有什么意思啊...</p><img src=" https://i.loli.net/2018/02/23/5a8f94da4261f.png"><p>有意思, Association 的原型果然是这个, 格式化用的是 Mathematica 的格式化, 因为按照浮点运算</p>

```js
> Math.log(1000) / Math.LN10
< 2.9999999999999996```

<p>文档里还有个运行 py 脚本的例子, 但是只能以字符串返回...那有什么意思...</p><h2>点评</h2><p>这玩意儿现在几乎没啥用, 这种功能 RunProcess + json + Interpreter 就能搞定</p><p>何况现在有了 WolframScript 我为什么不写 bash 脚本呢?</p><p>什么时候能交换绘制的图片啊, 函数啊, 神经网络啊什么的才牛逼了.</p><p>不过这个应该可以用来实现类似 Jupyter 的功能...</p><p>Notebook 左边这个小加号是能扩展的, 未来加个 Python 语言输入, Julia 语言输入也不是不可以啊...</p><img src=" https://i.loli.net/2018/02/23/5a8f94da42687.png"><hr/><p>Update 2018-09-10</p><p>一语成谶了啊, Mathematica 真的加入了 Python Cell 和 JavaScript Cell!</p>