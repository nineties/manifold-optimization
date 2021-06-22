---
title: 4. 多様体の様々な構成
section: 4
---

{{% definition title="多様体の直和" %}}
$d$次元 多様体 $(\mathcal{M},\mathcal{A}),(\mathcal{N},\mathcal{B})$ に対して

$$ (\mathcal{M}\sqcup\mathcal{N},\mathcal{A}\sqcup\mathcal{B}) $$

も$d$次元多様体となる。これを $\mathcal{M},\mathcal{N}$の **直和(disjoint union)** という。
{{% /definition %}}

共通部分がない2つの多様体を持ってきて、まとめて1つの多様体だと言っているだけなので、これ自体はあまり面白くないが、商空間を用いた構成の前段で直和を構成する場合がある。

例えば {{< ref ex.y-shape-space >}} では、まず2つの直線を持ってきて(これが$\mathbb{R}$と$\mathbb{R}$の直和)、商集合を作るという操作をしている。

{{% definition title="積多様体" %}}
$m$次元多様体 $(\mathcal{M},\mathcal{A})$ と $n$ 次元多様体 $(\mathcal{N},\mathcal{B})$ について直積

$$\mathcal{M}\times\mathcal{N}$$

は$m+n$ 次元多様体となる。これを $\mathcal{M},\mathcal{N}$ の **積多様体(product manifold)** という。積多様体の位相は $\mathcal{M},\mathcal{N}$ の積位相と一致する。

$$
\begin{aligned}
&\mathcal{C} = \\{(U\times V,\varphi\times\psi)|(U,\varphi)\in\mathcal{A},(V,\psi)\in\mathcal{B}\\} \\\\
&\text{但し} \varphi\times\psi:(x,y)\mapsto(\varphi(x),\psi(y)) \\\\
\end{aligned}
$$

とすると $\mathcal{C}^+$ が $\mathcal{M}\times\mathcal{N}$ の極大アトラスである。

{{% /definition %}}

例えばユークリッド空間 $\mathbb{R}^d$ は積多様体 $\mathbb{R}\times\cdots\times\mathbb{R}$ である。また、 **2-トーラス(2-torus)** $T^2$ は単位円 $S^1$ 2つの積である。($ T^2 = S^1\times S^1 $)

---

続いて多様体 $\mathcal{M},\mathcal{N}$ の間の写像 $F:\mathcal{M}\rightarrow\mathcal{N}$ としてどんなものを考えると便利かを考えるが、ユークリッド空間ではない一般の多様体上で定義された $F$ の微分可能性を述べるのは難しい。そこでチャートを利用する。

{{% definition title="座標表示" %}}
$m$次元多様体 $\mathcal{M}$ と $n$次元多様体$\mathcal{N}$ の間の写像 $F:\mathcal{M}\rightarrow\mathcal{N}$ と点 $x\in \mathcal{M}$ に対して、

$x$ を含む $\mathcal{M}$ のチャート $\varphi:U\rightarrow \varphi(U),\ x\in U$ と
$F(x)$ を含む $\mathcal{N}$ のチャート $\psi:V\rightarrow \psi(V),\ x\in V$ を用いた写像

$$ \psi\circ F\circ\varphi^{-1}:\mathbb{R}^m\rightarrow\mathbb{R}^n $$

を $F$ の点 $x$ の周りでの $\varphi,\psi$ による **座標表示(coordinate representation)** という。
{{% /definition %}}

