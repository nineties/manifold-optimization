---
title: 4. 可微分写像、部分多様体
section: 4
---

多様体と多様体の関係性について調べたりする時に、それらの間の写像 $F:\mathcal{M}\rightarrow\mathcal{N}$ について考える。多様体ではその微分構造に関心があるので $F$ も何らかの微分可能な写像を考える必要があるが、一般の多様体上で定義された $F$ の微分可能性を直接述べるのは難しい。そこで、チャートを利用する。

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
$m$ 次元多様体 $\mathcal{M}$ から、 $n$ 次元多様体 $\mathcal{N}$ への可微分写像$F:\mathcal{M}\rightarrow\mathcal{N}$, 点 $x\in\mathcal{M}$ に対して、線型写像 $\mathrm{D}_{\hat{F}}(\varphi(x))[-]:\mathbb{R}^m\rightarrow\mathbb{R}^n$ のランクを $F$ の 点 $x\in\mathcal{M}$ における **ランク(rank)** という。(全ての点でランクが等しい時は、それを 単に $F$ のランクという。)
{{% /definition %}}

微分同相写像$f: \mathbb{R}^n\rightarrow\mathbb{R}^n$ のヤコビ行列は正則行列になるので、座標変換によって可微分写像のランクは変わらない。

{{% definition title="はめ込みと沈め込み" %}}
$m$ 次元多様体 $\mathcal{M}$ から $n$ 次元多様体 $\mathcal{N}$ への可微分写像 $F:\mathcal{M}\rightarrow\mathcal{N}$ について

- $F$ のランクが $m$ である時、$F$ を **はめ込み(immersion)**
- $F$ のランクが $n$ である時、$F$ を **沈めこみ(submersion)**

と呼ぶ。
{{% /definition %}}

言い方を変えると $F$ がはめ込みであるとは、微分 $\mathrm{D}_f(x)[-]$ が全ての点$x$で単射であるという事であり、 沈めこみであるとは全射である事。各点での微分の単射性、全射性について言っているのであって、 $F$ そのものの単射性、全射性についてでは無いので注意。

{{% definition title="埋め込み" %}}
可微分写像 $:\mathcal{M}\rightarrow\mathcal{N}$ がはめ込みかつ単射であり、 $F(\mathcal{M})$ に $\mathcal{N}$ の相対位相を入れた時に $\mathcal{M}$ と $F(\mathcal{M})$ が同相となるならば $F$ を **埋め込み(embedding)** という。
{{% /definition %}}

例えば8の字を描く $F:(-\pi/2,3\pi/2)\rightarrow\mathbb{R}^2:t\mapsto(\sin 2t,\cos t)$  を考えると、これははめ込みかつ単射になっているが、埋め込みではない。

{{% definition title="部分多様体" %}}
$\mathcal{M},\mathcal{N}$ を $\mathcal{M}\subset\mathcal{N}$ であるような多様体とする。

包含写像 $i:\mathcal{M}\rightarrow\mathcal{N}:x\mapsto x$ がはめ込みである時、 $\mathcal{M}$ は $\mathcal{N}$ に **はめ込まれた部分多様体(immersed submanifold)** であるという。

また、$i$ が埋め込みである時、 $\mathcal{M}$ を $\mathcal{N}$ に **埋め込まれた部分多様体(embedded submanifold)** もしくは単に **部分多様体(submanifold)** という。
{{% /definition %}}

