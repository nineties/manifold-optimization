---
title: 5. 多様体の様々な構成と可微分写像
section: 5
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


{{% definition title="はめ込みと沈め込み" %}}
$m$ 次元多様体から $n$ 次元多様体への可微分写像 $F:\mathcal{M}\rightarrow\mathcal{N}$ の任意の点でのランクが $m$ である時、 $F$ を **はめ込み(immersion)** という。
ランクが $n$ である時は、**沈め込み(submersion)** という。
{{% /definition %}}
