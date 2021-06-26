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

写像 $F:\mathcal{M}\rightarrow\mathcal{N}$ の微分可能性について考えたいが、一般の多様体上で定義された $F$ の微分可能性を直接述べるのは難しい。そこでチャートを利用してユークリッド空間に移す。

{{% definition title="座標表示" %}}
$m$次元多様体 $\mathcal{M}$ と $n$次元多様体$\mathcal{N}$ の間の写像 $F:\mathcal{M}\rightarrow\mathcal{N}$ と点 $x\in \mathcal{M}$ に対して、

$x$ を含む $\mathcal{M}$ のチャート $\varphi:U\rightarrow \varphi(U),\ x\in U$ と
$F(x)$ を含む $\mathcal{N}$ のチャート $\psi:V\rightarrow \psi(V),\ x\in V$ を用いた写像

$$ \hat{F}=\psi\circ F\circ\varphi^{-1}:\mathbb{R}^m\rightarrow\mathbb{R}^n $$

を $F$ の点 $x$ の周りでの $\varphi,\psi$ による **座標表示(coordinate representation)** という。
{{% /definition %}}

{{< figure src="../images/coordinate-representation.png" >}}

$f:\mathbb{R}^m\rightarrow\mathbb{R}^n$ の微分可能性の定義を復習する。

{{% definition %}}
$f:\mathbb{R}^m\rightarrow\mathbb{R}^n$ が点 $a\in\mathbb{R}^m$ で **微分可能(differentiable)** であるとは

$$ \lim_{h\rightarrow 0}\frac{||f(a+h)-f(a)-\mathrm{D}_f(a)[h]||}{||h||}=0 $$ 

を満たす線型写像: $\mathrm{D}_f(a)[-]:\mathbb{R}^m\rightarrow\mathbb{R}^n$ が存在する事である。$f$ が任意の点で微分可能である事を、 $f$ は微分可能であるという。

$\mathrm{D}_f(a)[-]$ を $f$ の $a$ における **微分(differential)** という。

$\mathrm{D}_f(a)[h]$ を $f$ の $a$ における $h$ に沿った **方向微分(directional derivative)** という。
{{% /definition %}}

これは $f:\mathbb{R}\rightarrow\mathbb{R}$ の微分係数の一般化になっている。

$$
f(a+h) = f(a) + \mathrm{D}_f(a)[h] + o(||h||)
$$

であるので点 $a$ から $h$ だけ進むと $f(a)$ が $\mathrm{D}_f(a)[h]$ だけ増えるということ。 $\mathrm{D}_f(a)[-]$ が(写像だけど)接線の傾きに相当する。

$x=a+h$ とおいて書き直すと

$$
f(x) = f(a) + \mathrm{D}_f(a)[x-a] + o(||x-a||)
$$

であるので、これは $f(x)$ の $x=a$ の周りでの一次近似であるとも言える。

{{% proposition title="ヤコビ行列" %}}
$f:\mathbb{R}^m\rightarrow\mathbb{R}^n$ の点 $a$ での微分係数 $\mathrm{D}_f(a)[-]$ の標準基底での表現行列は **ヤコビ行列(Jacobian matrix)** $J_f(a)$ である。すなわち
$$ f: (x_1,\ldots,x_m)\mapsto (f_1(x_1,\ldots,x_m),\ldots,f_n(x_1,\ldots,x_m))$$
とおくと
$$
J_f(a) = \begin{pmatrix}
\frac{\partial f_1}{\partial x_1}(\mathbf{a}) & \cdots & \frac{\partial f_1}{\partial x_m}(\mathbf{a}) \\\\
\vdots & \ddots & \vdots \\\\
\frac{\partial f_n}{\partial x_1}(\mathbf{a}) & \cdots & \frac{\partial f_n}{\partial x_m}(\mathbf{a})
\end{pmatrix}
$$
である。
{{% /proposition %}}

つまり、標準基底では方向微分がヤコビ行列と $h$ の単なる積になる。

$$
\mathrm{D}_f(a)[h] = J_f(a)h
$$

$f:\mathbb{R}^m\rightarrow\mathbb{R}^n$ が微分可能ならば、各変数について偏微分可能であるがこの逆は成り立たない。一方、各偏微分係数が連続なら($f$が $C^1$ 級ならば)微分可能である事が言える。

{{% proposition %}}

$f:\mathbb{R}^{m_1}\rightarrow\mathbb{R}^{m_2}$ が $x$ で微分可能で $g:\mathbb{R}^{m_2}\rightarrow\mathbb{R}^{m_3}$ が $f(x)$ で微分可能ならば以下の連鎖律が成り立つ。

$$
\mathrm{D}_{g\circ f}(x) = \mathrm{D}_g(f(x))\circ\mathrm{D}_f(x)
$$
{{% /proposition %}}

{{% definition title="可微分写像" %}}
$F:\mathcal{M}\rightarrow\mathcal{N}$ が **可微分(differentiable)** であるとは、任意の点 $x\in\mathcal{M}$ について、その周りでの $F$ の座標表示

$$ \hat{F}=\psi\circ F\circ\varphi^{-1}:\mathbb{R}^m\rightarrow\mathbb{R}^n $$

が 点 $\varphi(x)\in\mathbb{R}^m$ で$C^\infty$ 級である事をいう。これはチャートの選び方によらない。
{{% /definition %}}

チャートの選び方によらないのは、多様体の任意の座標変換は微分同相であるから。

{{% definition title="微分同相写像" %}}
$F:\mathcal{M}\rightarrow\mathcal{N}$ が全単射で $F$ も $F^{-1}$ も可微分であるとき、$F$ を **微分同相写像(diffeomorphism)** という。

微分同相写像 $F:\mathcal{M}\rightarrow\mathcal{N}$ が存在するとき、$\mathcal{M},\mathcal{N}$ は **微分同相(diffeomorphic)** であるといい
$$ \mathcal{M}\simeq\mathcal{N}$$
と書く。
{{% /definition %}}

{{% definition title="可微分写像のランク" %}}
$m$ 次元多様体 $\mathcal{M}$ から、 $n$ 次元多様体 $\mathcal{N}$ への可微分写像$F:\mathcal{M}\rightarrow\mathcal{N}$, 点 $x\in\mathcal{M}$ に対して、線型写像 $\mathrm{D}_{\hat{F}}(\varphi(x))[-]:\mathbb{R}^m\rightarrow\mathbb{R}^n$ のランクを $F$ の 点 $x$ における **ランク(rank)** という。

{{% /definition %}}

可微分写像のランクもチャートの選び方に寄らない。

例として

$$f:S^2\rightarrow\mathbb{R}^3:(x,y,z)\mapsto(xy,x,y)$$

の微分とランクを求める。{{< ref ex.n-sphere >}} のチャート $\varphi_\pm$ を用いると

$$ f\circ\varphi_{\pm}^{-1}:\mathbb{R}^2\rightarrow\mathbb{R}^3: (u,v)\mapsto\left(\frac{4uv}{(u^2+v^2+1)^2},\frac{2u}{u^2+v^2+1},\frac{2v}{u2+v^2+1}\right)$$

となる。($\mathbb{R}^3$ 側はもともとユークリッド空間なので恒等関数をチャートにとすれば良い)

これらは、その定義域で $C^\infty$ 級なので微分可能。ヤコビ行列は

$$
J_f(u,v) = \frac{1}{(u^2+v^2+1)^3}\begin{pmatrix}
4v(v^2-3u^2+1) & 4u(u^2-3v^2+1) \\\\
2((v^2+1)^2-u^4) & -4uv(u^2+v^2+1) \\\\
-4uv(u^2+v^2+1) & 2((u^2+1)^2-v^4)
\end{pmatrix}
$$

((v^2+1)-u^2)((v^2+1)+u^2)
2((v^2+1)^2-u^4)


{{% definition title="はめ込みと沈め込み" %}}
$m$ 次元多様体から $n$ 次元多様体への可微分写像 $F:\mathcal{M}\rightarrow\mathcal{N}$ の任意の点でのランクが $m$ である時、 $F$ を **はめ込み(immersion)** という。
ランクが $n$ である時は、**沈め込み(submersion)** という。
{{% /definition %}}
