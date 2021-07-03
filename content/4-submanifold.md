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

{{% definition label="def.differential" %}}
$V,W$ をバナッハ空間(線型空間であって完備な距離を持つ)の間の写像 $f:V\rightarrow W$ が点 $a\in V$ で **微分可能(differentiable)** であるとは

$$ \lim_{h\rightarrow 0}\frac{||f(a+h)-f(a)-\mathrm{D}_f(a)[h]||}{||h||}=0 $$ 

を満たす線型写像: $\mathrm{D}_f(a)[-]:V\rightarrow W$ が存在する事である。$f$ が任意の点で微分可能である事を、 $f$ は微分可能であるという。

$\mathrm{D}_f(a)[-]$ を $f$ の $a$ における **微分(differential)** という。

$\mathrm{D}_f(a)[h]$ を $f$ の $a$ における $h$ に沿った **方向微分(directional derivative)** という。
{{% /definition %}}

バナッハ空間といっているが、ほとんどの場合はユークリッド空間 $\mathbb{R}^m$ であるか、行列 $\mathbb{R}^{m\times n}$ とフロベニウスノルム

$$ ||A||=\sqrt{\sum_{ij}a_{ij}^2} $$

からなる空間であるかどちらか。

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

例えば8の字を描く $F:(-\pi/2,3\pi/2)\rightarrow\mathbb{R}^2:t\mapsto(\sin 2t,\cos t)$  を考えると、これははめ込みかつ単射になっているが、埋め込みではない。というのは $(0,0)$ において $F^{-1}$ が不連続であるから。

{{< figure src="../images/8-shape-curve.png" >}}

---

多様体論では空間の内在的性質のみによってその特徴を調べていく方法が主に議論されるので、多様体の外側の空間というものを仮定しない場合が多い。しかし、多くの場面で(特にこのノートで扱う最適化問題の多くで)、別の多様体の部分集合となっている多様体を扱う事が多い。

例えば、$n$次元球面 $S^n$ は $n+1$次元多様体であるユークリッド空間 $\mathbb{R}^{n+1}$ の部分集合であり、 $S^n$ 自身も多様体である。($\mathbb{R}^{n+1}$ の部分多様体である)

$$
S^n=\\{\mathbf{x}\|\mathbf{x}\in\mathbb{R}^{n+1},||\mathbf{x}||=1\\}
$$


$m$次元多様体 $\mathcal{M}$ の部分集合 $\mathcal{N}$ が $n$ 次元多様体であるとは、局所的に $\mathbb{R}^n$ と同一視する事ができるという事であり、以下のように定義される。

{{% definition title="部分多様体" label="def.submanifold" %}}
$m$ 次元多様体 $\mathcal{M}$ が $n$ 次元多様体 $\mathcal{N}$ の部分集合($\mathcal{M}\subset\mathcal{N}$)である時、包含写像 $i:\mathcal{M}\rightarrow\mathcal{N}$ が埋め込みであるならば、 $\mathcal{M}$ を $\mathcal{N}$ の **部分多様体(submanifold)** という。
{{% /definition %}}

$\mathcal{M}$ が $\mathcal{N}$ の開集合であるならば開部分多様体、閉集合であるならば閉部分多様体という。 {{< ref prop.open-subset-is-manifold-of-samedimension >}} より $\mathcal{M}$ が開部分多様体ならば、$\mathcal{N}$ と同次元である。

以下を部分多様体の定義として用いる文献も多い。こちらは局所的に $\mathbb{R}^n$ と同一視できるという事を直接述べたものなので想像しやすいかもしれない。

証明は大変で詳しくは[Lee. Introduction to Smooth Manifolds](https://www.springer.com/jp/book/9780387217529) のTheorem 5.13を参照。

{{% proposition label="prop.definition-of-submanifold2" %}}
$n$ 次元多様体 $\mathcal{N}$ の部分集合 $\mathcal{M}$ が $m$ 次元部分多様体であるならば、任意の点 $x\in\mathcal{M}$ に対して、 それを含む $\mathcal{N}$ のチャート $(U,\varphi)$ が存在して
$$ \varphi(U\cap\mathcal{M})=\varphi(U)\cap(\mathbb{R}^n\times\\{0\\})$$
となる。すなわち $x\in U\cap\mathcal{N}$ において
$$\varphi(x)=(y_1,\ldots,y_n,0,\ldots,0)$$
となる。
$(U,\varphi)$ の事を $\mathcal{M}$ の **スライスチャート(slice chart)** という。
{{% /proposition %}}

実は $\mathcal{M}$ の微分構造は一意に定まる。従って、部分多様体について言及するときに、わざわざそのアトラスについては説明しない事が多い。 

{{% proposition %}}
多様体 $\mathcal{N}$ の部分集合 $\mathcal{M}$ が部分多様体となるような $\mathcal{M}$ の微分構造は一意に定まる。
{{% /proposition %}}

ある部分集合が部分多様体である事を示すのをチャートを具体的に計算して示すのは面倒だし、そもそもチャートの式が陽には表せない場合が多いので、以下のような定理を用いる。

{{% theorem label="th.submersion-theorem" %}}
$m$次元多様体 $\mathcal{M}$, $n$次元多様体 $\mathcal{N}$ ($m\geq n$)、可微分写像 $F:\mathcal{M}\rightarrow\mathcal{N}$、 点 $p\in\mathcal{N}$ について、 $F^{-1}(p)$ の全ての点で $F$ のランクが $n$ であるならば、 $F^{-1}(p)$ は $m-n$ 次元部分多様体である。

(このような $p$ を $F$の **正則値(regular value)** であるという。)
{{% /theorem %}}

$F^{-1}(p)$ の $n$ 次元分が一点に潰れるので $m-n$ 次元分が残るというイメージ。

{{< figure src="../images/submersion-theorem.png" >}}

これは非常に便利な定理でいろいろな集合が多様体である事を示すことができる。

例えば $ F:\mathbb{R}^{n+1}\rightarrow\mathbb{R}:x\mapsto||x||^2 $ について考えると、これは可微分であってヤコビ行列は

$$ J_F(x) = \begin{pmatrix}
2x_1 & \cdots & 2x_{n+1}
\end{pmatrix} $$

となるので $x=0$ 以外の点では $F$ のランクは1。従って例えば$1\in\mathbb{R}$ の逆像 $F^{-1}(1)$ は$(n+1)-1=n$ 次元部分多様体。実は $F^{-1}(1)=\\{x\in\mathbb{R}^{n+1}\mid ||x||^2=1\\}$ なので$n$ 次元超球面 $S^n$ が$n$ 次元多様体である事がこれで示された。

{{% example title="特殊線型群" %}}
**特殊線型群(special linear group)**
$$ SL_n = \\{X\in\mathbb{R}^{n\times n}\mid\det X=1\\}$$
は $n^2-1$ 次元多様体である。
{{% /example %}}

$F:\mathbb{R}^{n\times n}\rightarrow \mathbb{R}:X\mapsto \det X$ とすると $SL_n=F^{-1}(1)$ である事より。

{{% example title="直交群" %}}
**直交群(orthogonal group)**
$$ O_n = \\{X\in\mathbb{R}^{n\times n}\mid X^TX=I \\\}$$
は $n(n-1)/2$ 次元多様体である。
{{% /example %}}

$\mathrm{Sym}_n$ を$n$次実対称行列の集合とする。 これは上三角の $n(n+1)/2$ 要素を取り出す写像をチャートとすれば $n(n+1)/2$次元の多様体である事が分かる。

ここで $F:\mathbb{R}^{n\times n}\rightarrow\mathrm{Sym}_n: X^T\mapsto XX$ とすると $O_n=F^{-1}(I)$である。$F$ が可微分なのは(加減乗算だけなので)明らかなので、あとは $F$ のランクを計算する。

ここで $F$ の微分は
$$\mathrm{D}_F(X)[-]:H\mapsto X^TH+H^TX$$
となる。なぜならば$F(X+H)-F(X)-\mathrm{D}_F(X)[H] = H^TH$
で $\lim\_{H\rightarrow 0}||H^TH||/||H||\rightarrow 0$ であるから。

ここで任意の $Y\in\mathrm{Sym}_n$ に対して $H=XY/2$ とおくと

$$\mathrm{D}_F(X)\left[\frac{XY}{2}\right]=\frac{1}{2}(X^T(XY)+(XY)^TX)=\frac{1}{2}(Y+Y^T)=Y$$

より $\mathrm{D}_F[-]$ はフルランクであるので、$F$ のランクは $n(n+1)/2$。従って  $O_n$ の次元は $n^2-n(n+1)/2=n(n-1)/2$

{{% example title="回転群" %}}
**回転群(rotation group)** もしくは **特殊直交群(special orthogonal group)**
$$ SO_n = \\{X\in\mathbb{R}^{n\times n}\mid X^TX=I,\det X=1 \\\}$$
は $n(n-1)/2$ 次元多様体である。
{{% /example %}}

$\mathbb{R}\_+$ を正の実数の集合とすると、これは $\mathbb{R}$ の開集合。$\det:\mathbb{R}^{n\times n}\rightarrow\mathbb{R}$ は連続写像だから $\det(\mathbb{R}\_+) \subset\mathbb{R}^{n\times n}$ も開集合。よって
$SO_n = O_n\cap\det(\mathbb{R}\_+)$
より $SO_n$ は $O_n$ の開部分集合であるので $O_n$ と次数の等しい多様体である。


{{% example title="コンパクトシュティーフェル多様体" label="ex.stiefel-manifold" %}}
$p\leq n$ の時
$$\mathrm{St}(p,n)=\\{X\in\mathbb{R}^{n\times p}\mid X^TX = I_p\\}$$
を **コンパクトシュティーフェル多様体(compact Stiefel manifold)** という。これは $np-p(p+1)/2$ 次元多様体である。
{{% /example %}}

コンパクトシュティーフェル多様体は $p=1$ の時は $n-1$ 次元球面、 $p=n$ の時は直交群になり、これらを一般化したものと言える。証明は直交群とほぼ同じなので省略。
