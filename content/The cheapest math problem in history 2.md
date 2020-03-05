+++
title = "史上最贱数学题(番外)"
date = 2017-09-16
[taxonomies]
tags = ["insane problems"]
categories = ["Math", "Number Theory"]
+++

<p>这个题其实相当显然, 因为:</p><p class="math">$$\begin{aligned}
f=&\frac{a}{b+c}+\frac{b}{a+c}+\frac{c}{a+b} \\
=&\frac{3}{2} + \frac{1}{2} \left(\frac{(a-b)^2}{(a+c)(b+c)}+\frac{(a-c)^2}{(a+b)(b+c)}+\frac{(b-c)^2}{(a+b)(a+c)}\right)\\
\geq &\frac32\qquad \mathtt{quiet\ easily\ done!}
\end{aligned}$$</p> <p>角豆麻袋, 什么情况, 不要使用禁咒 <span class="math">$\cdot$</span>  陈计配凑, 好吗!</p><p>你能不能按照<b>高考考纲</b>以及<b>高考给分要求</b>来啊?</p><p>说的是呢, 其实也不是很难, 换个元更清晰.</p><p>解: 设 <span class="math">$a+b:=x,b+c:=y,c+a:=z$</span> .</p><p class="math">$$\begin{aligned}
2f=&2 \left(\dfrac{a}{b+c}+\dfrac{b}{c+a}+\dfrac{c}{a+b}\right)\\
=&\dfrac{a+a}{y}+\dfrac{b+b}{z}+\dfrac{c+c}{x}\\
=&\dfrac{z-c+x-b}{y}+\dfrac{x-a+y-c}{z}+\dfrac{y-b+z-a}{x}\\
=&\dfrac{z+x-y}{y}+\dfrac{x+y-z}{z}+\dfrac{y+z-x}{x}\\
=&\underbrace{\dfrac{x}{y}+\dfrac{y}{x}}_{\geq 2}+\underbrace{\dfrac{y}{z}+\dfrac{z}{y}}_{\geq 2}+\underbrace{\dfrac{z}{x}+\dfrac{x}{z}}_{\geq 2}-3 \\
\geq &3 \qquad\mathtt{Q.E.D}
\end{aligned}$$</p> <p>答: 由是观之, <span class="math">$\dfrac{a}{b+c}+\dfrac{b}{c+a}+\dfrac{c}{a+b}\geq \dfrac32$</span> .</p><p>很自然的想到, 是不是能有:</p><p class="math">$$\sum_{i=1}^{n} \frac{x_i}{x_{i+1}+x_{i+2}} \geq \frac{n}{2}$$</p> <p>n=3是个很有名的情形, Nesbitt's_inequality,有十几种证明, <span class="math">$n=4$</span>  还可以通过观察法凑配, <span class="math">$n=5,6$</span> 要借助凸性构造Jensen不等式, 接下来难度开始爆炸, 各种玄妙的操作...</p><p>最后.......</p><hr/><p>很不幸, 这不是恒成立的, 当n=14时崩坏了...</p><p>Troesch 给出了一个反例:</p><p class="math">$$x_{14}=(0,42,2,42,4,41,5,39,4,38,2,38,0,40)$$</p> <p class="math">$$\sum_{cyc}^{x_{14}}\frac{x_i}{x_{i+1}+x_{i+2}}=\frac{202566829}{28938140}\approx6.999999<\frac{14}{2}$$</p>

```mathematica
var={0,42,2,42,4,41,5,39,4,38,2,38,0,40};
#1/(#2+#3)&@@@Partition[var,3,1,1]//Total```

<p>哇, 有毒啊, 构造大丈夫....</br>事实上这个不等式只对 <span class="math">$n=3\sim14,15,17,19,21,23$</span>  成立.</p><p>Shapiro inequality is an inequality proposed by H. Shapiro in 1954.</p><p>借助一些分析学手段发现可以打个补丁修正这个不等式:</p><p class="math">$$\sum_{i=1}^{n} \frac{x_i}{x_{i+1}+x_{i+2}} \geq \frac{\gamma}{2}n$$</p> <p><span class="math">$\gamma$</span>  是 <span class="math">$y_1(x)=e^{-x}$</span>  与 <span class="math">$y_2(x)=\dfrac{2}{e^{x/2}+e^x}$</span>  的函数凸包的根...</p><blockquote><p><b>FunctionConvexHull</b></br>The convex hull of two or more functions is the largest function that is concave from above and does not exceed the given functions.</p></blockquote><p>我也不知道函数凸包是什么鬼, 描述和下面的计算完全对不上......</p><p>具体来说就是下列方程的实根:</p><p class="math">$$x+\frac{1}{2 e^{x/2}+1}=\log \left(\frac{4 e^x}{2 e^{x/2}+1}\cosh ^2\left(\frac{x}{4}\right)\right)$$</p> <p>就一个, 代入下面这个式子里...</p><p class="math">$$\gamma=\frac{1}{4} \left(2 e^{-\frac{x}{2}} (x+1)+e^{-x} (x+2)\right) \text{sech}^2\left(\frac{x}{4}\right)$$</p>

```mathematica
eq=1/(1 + 2*E^(x/2)) + x == Log[(4*E^x*Cosh[x/4]^2)/(1 + 2*E^(x/2))];
r=FindRoot[eq, {x, -1},WorkingPrecision->50];
(1/4)*Sech[x/4]^2*((2 + x)/E^x + (2*(1 + x))/E^(x/2)) /.r

>>0.98913363444699305224349030826633798138034809804418```

<p>http://www.turgor.ru/lktg/2010/5/5-1en.pdf</br>https://en.wikipedia.org/wiki/Shapiro_inequality</br>http://mathworld.wolfram.com/ShapirosCyclicSumConstant.html</br>https://en.wikipedia.org/wiki/Nesbitt%27s_inequality</p>
