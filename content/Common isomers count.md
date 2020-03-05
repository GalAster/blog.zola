+++
title = "常见同分异构体计数"
date = 2018-03-04
[taxonomies]
categories = ["Chemistry", "Combinatorics"]
+++

<h1>引言</h1><h1>计算</h1><h2>烷基自由基计数</h2><p>我们从卤代烃<span class="math">$C_nH_{2n+1}X$</span> 开始, X是卤素, 当然也可以是别的取代基.</p><h3>Planarisomers</h3><p>设 Free radicals count ,<span class="math">$\mathtt{Fr}(x)$</span> </p><p>三个取代基的置换群若不考虑手性为 S_3 ;若考虑手性为 A_3 <pre>\cong{}</pre> <pre>\mathbb{\Z{}}</pre>_3</p><p class="math">$$\mathbb{Z}(\mathcal{S}_3)=\frac 16 (2s_3+3s_2s_1+s_1^3)$$</p> <p>补上剩下的一个碳</p><p class="math">$$\begin{aligned}
A(x)&=1+x\mathbb{Z}[\mathcal{S}_3,A(x)]\\
&=1+\dfrac{x}{6}[A^3(x)+3A(x)A(x^2)+2A(x^3)]
\end{aligned}$$</p> <p>当然这个函数方程怎么展开是个大问题, 我们可以使用附录中级数的复合与反演来解决.</p>

```mma
A[z_]:=Evaluate@Normal@Fold[
Series[1+z/6(#^3+3# ComposeSeries[#,z^2+O[z]^#2]+2 ComposeSeries[#,z^3+O[z]^#2]),{z,0,#2}]&,
1+O[z],Range@Floor@n
];```

<h3>Stereoisomers</h3><p>三个取代基的置换群若考虑手性为循环群 <span class="math">$\mathcal{C}_3$</span> </p><p class="math">$$\mathbb{Z}(\mathcal{C}_3)=\frac13(s_1^3+2 s_3)$$</p>

```mma
A[z_]:=Evaluate@Normal@Fold[
Series[1+z/3(#^3+2 ComposeSeries[#,z^3+O[z]^#2]),{z,0,#2}]&,
1+O[z],Range@Floor[n/2]
];```

<h2>烷烃计数</h2><p>接下来考虑从烷基自由基组合生成烷烃 <span class="math">$C_nH_{2n+2}$</span> </p><p class="math">$$p^*-q^*+s=1$$</p> <p>点的等价类数-边的等价类数+对称边数=1</p><p>碳的不同标记方法数-键的不同标记方法数+对称键数=1</p><p>let Alkane Count,<span class="math">$\mathtt{Ac}$</span> </p><pre>\mathtt{\Ac{}}</pre><p>(z)=P(z)-Q(z)+S(z)</p><h3>Planarisomers</h3><p class="math">$$\begin{aligned}
P(x)&=x\mathbb{Z}[\mathcal{S}_4,A(x)]\\
&=\frac{1}{24}x(A^4(x)+6A^2(x)A(x^2)+3A^2(x^2)+8A(x)A(x^3)+6A(x^4))\\
Q(x)&=\mathbb{Z}[\mathcal{S}_2,A(x)-1]\\
&=\frac 12((A(x)-1)^2+A(x^2)-1)\\
S(x)&=A(z^2)-1
\end{aligned}$$</p>

```mma
AlkaneSeries[n_Integer]:=Block[
{A,P,Q,S,G},
A[z_]:=Evaluate@Normal@Fold[
Series[1+z/6(#^3+3# ComposeSeries[#,z^2+O[z]^#2]+2 ComposeSeries[#,z^3+O[z]^#2]),{z,0,#2}]&,
1+O[z],Range@Floor[n/2]
];
P[z_]=z CycleIndexPolynomial[SymmetricGroup[4],Array[A[z^#]&,4]];
Q[z_]=CycleIndexPolynomial[SymmetricGroup[2],Array[A[z^#]-1&,2]];
S[z_]=A[z^2];
Series[P[z]-Q[z]+S[z]-1,{z,0,n}]
];```

<h3>Stereoisomers</h3><p>同样的 <span class="math">$p^*$</span>  由对称群<span class="math">$\mathcal{S}_4$</span>  变为交错群<span class="math">$\mathcal{A}_4$</span> .</p><p class="math">$$\mathbb{Z}(\mathcal{A}_4)=\frac{1}{12}(s_1^4+8 s_3 s_1+3 s_2^2)$$</p> <p class="math">$$Q(x)=\mathbb{Z}[\mathcal{A}_4,A(x)]=\frac{1}{12}\left(8 A\left(z^3\right) A(z)+3 A\left(z^2\right)^2+A(z)^4\right)$$</p>

```mma
AlkaneSeries[n_Integer]:=Block[
{A,P,Q,S,G},
A[z_]:=Evaluate@Normal@Fold[
Series[1+z/3(#^3+2 ComposeSeries[#,z^3+O[z]^#2]),{z,0,#2}]&,
1+O[z],Range@Floor[n/2]
];
P[z_]=z CycleIndexPolynomial[AlternatingGroup[4],Array[A[z^#]&,4]];
Q[z_]=CycleIndexPolynomial[SymmetricGroup[2],Array[A[z^#]-1&,2]];
S[z_]=A[z^2];
Series[P[z]-Q[z]+S[z]-1,{z,0,n}]
];```

<h2>苯环</h2>

```
pg = GroupDirectProduct[AlternatingGroup@5, CyclicGroup@2];
A[z_, i_] := Evaluate[#^i & /@ (1 + a + b + c + d)]
CycleIndexPolynomial[pg, Array[A[z, #] &, 60]];
Coefficient[%, a b c d]```

<h1>附录</h1><h3>旋转群与指标多项式</h3><p>S,C,A,D</p><h3>级数复合与反演</h3><p>拉格朗日反演, 比起比较两边系数高到不知道哪里去了.</p><h3>群直积与积群</h3>

```mma
GroupDirectProduct[g1_,g2_]:=With[
{order1=GroupOrder@g1,order2=GroupOrder@g2,r,pd},
r=Thread[Range[order2]->(order1+Range[order2])];
pd=Outer[PermutationProduct,GroupElements[g1],GroupElements[g2]/.r];
PermutationGroup@Flatten@pd
]```

<p>我刚开始以为Mathematica没有计算群直积的函数, 然后写了个<code>GroupDirectProduct</code>.</p><p>后来才发现确实没有这个函数, 因为群直积居然划分在群属性里.</p>

```mma
GroupDirectProduct[AlternatingGroup@5,CyclicGroup@2]
FiniteGroupData[{"DirectProduct",
{
{"AlternatingGroup",5},
{"CyclicGroup",2}
}
},"PermutationGroupRepresentation"]```
