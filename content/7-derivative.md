---
title: 7. 微分
section: 7
---

{{< ref def.differential >}} で定めたバナッハ空間の間の写像 $f:V\rightarrow W$ の微分 $\mathrm{D}f(a)[-]$ を接ベクトル空間に対して一般化する。

{{% definition %}}
多様体の間の滑らかな写像 $F:\mathcal{M}\rightarrow\mathcal{N}$ と、接ベクトル $v=[\gamma]\in T_x\mathcal{M}$ に対して、
$$\mathrm{D}F(x)[v] := [F\circ\gamma]$$
と定めると $\mathrm{D}F(x)[v]$ は $\mathcal{N}$の$F(x)$ における接ベクトルとなる。この対応

$$ \mathrm{D}F(x):T_x\mathcal{M}\rightarrow T\_{F(x)}\mathcal{N}: v\mapsto\mathrm{D}F(x)[v] $$

は線型写像になり、これを $F$ の $x$ における **微分(differential)** という。
{{% /definition %}}

{{< figure src="../images/derivative.png" >}}

多様体上においても以下の連鎖律が成立する。

{{% proposition %}}
滑らかな写像 $F:\mathcal{L}\rightarrow\mathcal{M},\ G:\mathcal{M}\rightarrow{N}$ と、点 $x\in\mathcal{L}$、接ベクトル $v\in T_x\mathcal{L}$ に対して、
$$
\mathrm{D}(G\circ F)(x)[v] =\mathrm{D}G(F(x))[\mathrm{D}F(x)[v]]
$$
{{% /proposition %}}

$\mathcal{M},\mathcal{N}$ がベクトル空間の場合は同型 $T\_x\mathcal{M}\simeq\mathcal{M}, T\_{F(x)}\mathcal{N}\simeq\mathcal{N}$ によって $v$ は普通のベクトル $v\in\mathcal{M}$ となり、 $F$ の微分は

$$ \mathrm{D}F(x)[v] = \lim\_{t\rightarrow 0}\frac{F(x+vt)-F(x)}{t} $$

となって、普通の方向微分になる。以下、ベクトル空間上の関数の微分公式を示していく。

{{% proposition %}}
線型写像 $F:\mathcal{M}\rightarrow\mathcal{N}$ に対して
$$ \mathrm{D}F(x)[v] = F(v) $$
{{% /proposition %}}

$F$ が線型写像ならば $F(x+vt)=F(x)+tF(v)$ である為。

{{% proposition %}}
$$ \mathrm{D}\\,\mathrm{tr}(X)[V] = \mathrm{tr}(V) $$
{{% /proposition %}}
$\mathrm{tr}:\mathbb{R}^{n\times n}\rightarrow\mathbb{R}$ は線型写像である為。

{{% proposition %}}
$\mathrm{inv}:\mathrm{GL}_n\rightarrow\mathrm{GL}_n: X\mapsto X^{-1}$ とすると
$$ \mathrm{D}\\,\mathrm{inv}(X)[V] = -X^{-1}VX^{-1} $$
{{% /proposition %}}

$$\begin{aligned}
\mathrm{D}\\,\mathrm{inv}(X)[V] &= \lim_{t\rightarrow 0}\frac{(X+tV)^{-1}-X^{-1}}{t} \\\\
&= \lim_{t\rightarrow 0}(X+tV)^{-1}\frac{I-(X+tV)X^{-1}}{t} \\\\
&= -\lim_{t\rightarrow 0}(X+tV)^{-1}VX^{-1}\\\\
&= -X^{-1}VX^{-1} \qquad\square
\end{aligned} $$

{{% proposition %}}
$\mathrm{det}:\mathrm{GL}_n\rightarrow\mathbb{R}$ に対して
$$ \mathrm{D}\\,\mathrm{det}(X)[V] = \mathrm{tr}\left(\mathrm{adj}(X)V\right) = \mathrm{det}(X)\mathrm{tr}\left(X^{-1}V\right) $$
{{% /proposition %}}

$$\begin{aligned}
\mathrm{D}\\,\mathrm{det}(X)[V] &= \lim_{t\rightarrow 0}\frac{\mathrm{det}(X+tV)-\mathrm{det}(X)}{t} \\\\
 &= \mathrm{det}(X)\lim_{t\rightarrow 0}\frac{\mathrm{det}(I+tX^{-1}V)-1}{t} \\\\
\end{aligned} $$

である。ここで $\mathrm{det}(I+tA)$ を $t$ について展開すると

$$\mathrm{det}(I+tA) = 1 + \mathrm{tr}(A) t + o(t^2)$$

となるので

$$\mathrm{D}\\,\mathrm{det}(X)[V] = \mathrm{det}(X)\lim_{t\rightarrow 0}(\mathrm{tr}(X^{-1}V)+o(t))=\mathrm{det}(X)\mathrm{tr}(X^{-1}V) \qquad\square$$
