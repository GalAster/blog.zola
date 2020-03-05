+++
title = "Generating Function Transformation"
date = 2018-01-17
[taxonomies]
+++

<h3>引言</h3><p>生成函数</p><p>数列变换和函数变换</p>

<!-- more -->

<h2>数列变换</h2><h3>加和原理</h3><p class="math">$$\sum_{n\geq0}(f_n+g_n)x^n=F(z)+G(z)$$</p> <p>数列和等于函数和, 收敛域依赖于小的那个函数.</p><h3>位移原理</h3><h3>Hadamard 积</h3><p>两个数列的乘积称为 Hadamard 积</br><span class="math">$\displaystyle{\sum_{n\geq 0}f_{n}g_{n}z^{n}:=(F\odot G)(z)={\frac {1}{2\pi }}\int_{0}^{2\pi }F\left({\sqrt {z}}e^{\imath t}\right)G\left({\sqrt {z}}e^{-\imath t}\right)\mathrm{d}t}$</span> </p><h3>等比原理</h3><p class="math">$$\sum_{n\geq 1}\frac{f_n}{k^n}z^{n}=\sum_{n\geq 1}f_n\frac{z^n}{k^n}=F\left(\frac{z}{k}\right)$$</p> <h3>Zeta 变换</h3><h4>Zeta 主变换</h4><p>定义 <span class="math">$\displaystyle\left\{\begin{matrix}k+2\\j\end{matrix}\right\}_\ast:={\frac {1}{j!}}\times \sum_{m=1}^{j}{\binom {j}{m}}{\frac {(-1)^{j-m}}{m^k}}$</span> </p><p>那么数列<span class="math">$f_n$</span> 的 Zeta 变换可以记为:</p><p class="math">$$\sum_{n\geq 1}{\frac {f_{n}}{n^{k}}}z^{n}=\sum_{j\geq 1}\left\{\begin{matrix}k+2\\j\end{matrix}\right\}_{\ast }z^{j}F^{(j)}(z)$$</p> <p>where Then for <span class="math">$k \in \mathbb{Z}^{+}$</span>  and some prescribed OGF, <span class="math">${\displaystyle F(z)\in C^{\infty }}$</span> , i.e., so that the higher-order <span class="math">$j^{th}$</span>  derivatives of<span class="math">$F(z)$</span>  exist for all <span class="math">$j\geq 0$</span> , we have that</p><h4>Zeta 逆变换</h4><p class="math">$$\sum_{n\geq 0}n^{k}f_{n}z^{n}=\sum_{j=0}^{k}\left\{\begin{matrix}k\\j\end{matrix}\right\}z^{j}F^{(j)}(z)$$</p> <h4>Polylogarithm 级数</h4><h3>提取原理</h3><h4>奇偶提取</h4><p class="math">$$\begin{aligned}
&\sum _{n\geq 0}f_{2n}z^{2n}&={\frac {1}{2}}\left(F(z)+F(-z)\right)\\
&\sum _{n\geq 0}f_{2n+1}z^{2n+1}&={\frac {1}{2}}\left(F(z)-F(-z)\right)
\end{aligned}$$</p> <h5>五级标题</h5><h6>六级标题</h6><h3>Borel 变换</h3><p>Borel 变换描述了OGF与EGF间的转换关系.</p><p class="math">$$\begin{aligned}
F(z)&=\sum _{n\geq 0}f_{n}z^{n}=\int _{0}^{\infty }{\hat {F}}(tz)e^{-t}dt\\
\hat {F}(z)&=\sum _{n\geq 0}{\frac {f_{n}}{n!}}z^{n}={\frac {1}{2\pi }}\int _{-\pi }^{\pi }F\left(ze^{-\imath \vartheta }\right)e^{e^{\imath \vartheta }}d\vartheta
\end{aligned}$$</p> <hr/><h2>函数变换</h2><h3>加和原理</h3><p class="math">$$\sum_{n\geq0}(f_n+g_n)x^n=F(z)+G(z)$$</p> <h3>Cauchy 积</h3><p class="math">$$ \sum (f *g)(n):=\left(\sum_{n=0}^\infty f_n x^n\right) \cdot \left(\sum_{n=0}^\infty g_n x^n\right) = \sum_{k=0}^\infty h_n x^n$$</p> <p>where <span class="math">$\displaystyle h_{k}=\sum_{l=0}^{k}f_{l}g_{k-l}$</span> .</p><h3>Faá di Bruno 复合</h3><p class="math">$$\hat{H}(z):=\hat {F}(\hat {G}(z))=\sum_{n=0}^{\infty }{\frac {h_n}{n!}}z^n$$</p> <p>where: <span class="math">$\displaystyle h_n=\sum_{1\leq k\leq n}f_k\cdot B_{n,k}(g_1,g_2,\cdots,g_{n-k+1})+f_0\cdot\delta_{n,0}$</span> </p><h3>取自幂</h3><p class="math">$$ F(z)^{m}=f_{0}^{m}+\sum_{n\geq 1}\left(\sum_{1\leq k\leq n}(m)_{k}f_{0}^{m-k}B_{n,k}(f_{1}\cdot 1!,f_{2}\cdot 2!,\ldots )\right){\frac {z^{n}}{n!}}$$</p> <h3>取对数</h3><p class="math">$$\log F(z)=\sum_{n\geq 1}\left(\sum_{1\leq k\leq n}(-1)^{k-1}(k-1)!B_{n,k}(f_{1}\cdot 1!,f_{2}\cdot 2!,\ldots )\right){\frac {z^{n}}{n!}}$$</p> <p>https://en.wikipedia.org/wiki/Generating_function_transformation</p>
