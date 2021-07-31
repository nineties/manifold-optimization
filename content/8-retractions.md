---
title: 8. レトラクション
section: 8
---

ユークリッド空間 $\mathbb{R}^n$ の関数 $f:\mathbb{R}^n\rightarrow\mathbb{R}$ に対する **直線探索法(line-search method)** とは点 $x_0\in\mathbb{R}^n$ から出発して、更新式

$$ x_{k+1}=x_k + t_kv_k $$

を反復し $f$ の極小値を求める方法。ここで $v_k$ は **探索方向(search direction)** と呼ばれるベクトル、 $t_k$ は **ステップサイズ(step size)** と呼ばれるスカラーであって、これらをどのように求めるかによって様々な最適化アルゴリズムが存在する。


これを多様体 $\mathcal{M}$ 上で行うためには、$v_k$ を点 $x_k$ での接ベクトル $T_{x_k}\mathcal{M}$ とし、 $\gamma$ を $\dot{\gamma}(0)=v_k$ となるような曲線とし、 $\gamma$ に沿って探索を行えば良い。

{{< figure src="../images/linesearch.png" >}}

ユークリッド空間での直線探索法と異なり、曲線 $\gamma$ の選び方という自由度が増えている。$\gamma$ を構成する方法は無数にあるが、レトラクションという写像を用いるのが一般的である。

{{% definition title="レトラクション" %}}
接バンドル $T\mathcal{M}$ から $\mathcal{M}$ への滑らかな写像 $R:T\mathcal{M}\rightarrow\mathcal{M}$ で以下の条件を満たすものを **レトラクション(retraction)** という。 $R$ の $T_x\mathcal{M}$ への制限を $R_x:T_x\mathcal{M}\rightarrow\mathcal{M}$ と書く。

1. $R_x(0) = x$
2. **局所剛性(local rigidity)** : $\mathrm{D}\_{R_x}(0)=\mathrm{id}_{T_x\mathcal{M}}$
{{% /definition %}}

$\mathrm{D}\_{R_x}(0)$ は $T_x\mathcal{M}$の接ベクトル空間 $T_0T_x\mathcal{M}$ から $T_x\mathcal{M}$ への写像
$$ \mathrm{D}\_{R_x}(0): T_0T_x\mathcal{M}\rightarrow T_x\mathcal{M} $$
であるが、$T_x\mathcal{M}$ はベクトル空間だから $T_0T_x\mathcal{M}\simeq T_x\mathcal{M}$ であるので
$$ \mathrm{D}\_{R_x}(0): T_x\mathcal{M}\rightarrow T_x\mathcal{M} $$
として上の定義では扱っている。

そして局所剛性は、任意の $v\in T_x\mathcal{M}$ に対して

$$\mathrm{D}\_{R_x}(0)[v] = v$$

であるということ。レトラクションが与えられると、直線探索を行うのに必要な曲線を以下のようにして構成することができる。

{{% proposition %}}
$R:T\mathcal{M}\rightarrow\mathcal{M}$ をレトラクションとする。接ベクトル $v\in T_x\mathcal{M}$ に対して曲線を
$$ \gamma(t) = R_x(tv) \quad t\in(-\varepsilon,\varepsilon)$$
と定めると
$$ \gamma(0) = x,\ \dot{\gamma}(0) = v $$
{{% /proposition %}}

$\gamma:(-\varepsilon,\varepsilon)\rightarrow\mathcal{M}$ が滑らかな写像であるのは明らかであり $\gamma(0)=R_x(0) = x$ かつ

$$\dot{\gamma}(0) = \mathrm{D}_{R_x}(0)\left[\frac{\mathrm{d}(tv)}{\mathrm{d}t}(0)\right] = \mathrm{D}\_{R_x}(0)[v]=v$$

{{< figure src="../images/retraction.png" >}}

$\mathcal{M}$ を多様体、 $\mathrm{R}$ を $\mathcal{M}$ の何らかのレトラクションとする。点 $x_k\in\mathcal{M}$ から接ベクトル $v_k\in T_{x_k}\mathcal{M}$ の方向にステップサイズ $t_k\in\mathbb{R}$ だけ進むという事は、更新式
$$ x_{k+1} = \mathrm{R}_{x_k}(t_kv_k) $$
によって表す事ができる。

このように、多様体上での最適化アルゴリズムはレトラクションの選び方によって変化し、効率的に計算できるレトラクションを見つける事が重要となる。

ちなみに、リーマ多様体には **指数写像(exponential mapping)** という自然に定まるレトラクションが存在するが、計算量が多く計算機で扱うのは難しい事が多い。

{{% example title="ベクトル空間のレトラクション" %}}
ベクトル空間 $\mathcal{M}$ の点 $x$ と、接ベクトル $v\in T_x\mathcal{M}$ に対して、同型 $\mathcal{M}\simeq T_x\mathcal{M}$ を用いて
$$ R_x(v) = x + v $$
と定めると、これはレトラクションである。
{{% /example %}}

$\mathcal{M}$ がベクトル空間の場合には(今定めたレトラクションを用いると)、更新式は

$$ x_{k+1} = \mathrm{R}_{x_k}(t_kv_k) = x_k + t_kv_k $$

となって、通常の直線探索と一致する。

続いて、$\mathcal{M}$ がベクトル空間 $\mathcal{V}$ の部分多様体である場合を考える。この場合も 点 $x\in\mathcal{M}$ と接ベクトル $v\in T_x\mathcal{M}$ の加算 $ x + v $ を$\mathcal{V}$ の中で求める事が出来る。従って $x+v$ を $\mathcal{M}$ の点に移す写像によってレトラクションを構成する事ができるが、以下がその写像が満たすべき条件となる。

{{% proposition label="prop.retraction" %}}
$\mathcal{M}$ をベクトル空間 $\mathcal{V}$ の部分多様体とし、 $\mathcal{N}$ を
$$ \dim \mathcal{M} + \dim \mathcal{N} = \dim\mathcal{V} $$
であるような任意の多様体とする。
$ \phi: \mathcal{M}\times\mathcal{N}\rightarrow \mathcal{V} $
を埋め込みであり、かつある点 $e\in\mathcal{N}$ が存在して
$$ \phi(x,e) = x\quad \forall x\in\mathcal{M} $$
となるものであるとする。また $\pi:\mathcal{M}\times\mathcal{N}\rightarrow\mathcal{V}:\pi(x,y)=x$ とする。このとき
$$ R_x(v) = \pi(\phi^{-1}(x + v)) $$
は $x$ の近傍で $\mathcal{M}$ のレトラクションである。
{{% /proposition %}}

{{% example title="$n$次元球面のレトラクションの例" %}}
$S^n$ 上の点 $x$ と $v\in T_x S^n$ に対して
$$\mathrm{R}_x(v) = \frac{x+v}{||x+v||} $$
{{% /example %}}

$\mathcal{M}=S^n, \mathcal{N}=\\{r\in\mathbb{R}\mid r > 0\\}$ に対して
$$\phi:S^n\times\mathcal{N}\rightarrow\mathbb{R}^{n+1}\_\ast: (x,r) \mapsto rx $$
とおき {{< ref prop.retraction >}} を使用。

直交群やシュティーフェル多様体に対するレトラクションの同様の構成は行列のQR分解を利用して得られる。

{{% proposition title="QR分解" %}}
$U^+_{n}$ を $n\times n$ の実上三角行列で対角成分が全て正であるものの集合とする。

任意の $X\in\mathbb{R}^{m\times n}_\ast, (m\geq n)$ は

$$ X=QR\quad (Q\in \mathbb{R}^{m\times n}, R\in U^+_n, Q^TQ=I)$$
と一意に分解できる。この対応 $X\mapsto Q$ を $\mathrm{qf}(X)=Q$ と表記する。

{{< figure src="../images/qr-factorization.png" >}}
{{% /proposition %}}

特に $m=n$ の時は $Q$ は直交行列となる。


{{% example title="直交群のQR分解によるレトラクション" %}}
直交群 $O_n$ の点 $X$ と $V=X\Omega\in T_XO_n$ に対して
$$ R_X(V) = \mathrm{qf}(X + V)=X\mathrm{qf}(I+\Omega) $$
{{% /example %}}

$\mathcal{M}=O_n,\mathcal{N}=U^+_{n}$ に対して
$$ \phi: O_n\times U^+_n\rightarrow\mathbb{R}^{n\times n}\_\ast: (Q,R)\rightarrow QR $$
とおく。$\dim O_n=n(n-1)/2, \dim U^+_n = n(n+1)/2$ より $\dim \mathbb{R}^{n\times n}\_\ast = \dim O_n + \dim U^+_n$ なので {{< ref prop.retraction >}} が使える。

ここで
$$ T_XO_n = X\mathrm{Skew}_n=\\{X\Omega\mid\Omega^T=-\Omega\\}$$
であったので $V=X\Omega$ と書けるから
$$\mathrm{R}_X(X\Omega)=\mathrm{qf}(X+X\Omega)=X\mathrm{qf}(I+\Omega)\quad(\because\text{$X$は直交行列})$$

とも表せる。

シュティーフェル多様体へ一般化しても全く同様。

{{% example title="シュティーフェル多様体のQR分解によるレトラクション" %}}
シュティーフェル多様体 $\mathrm{St}(p,n)$ の点 $X$ と $V=T_X\mathrm{St}(p,n)$ に対して
$$ R_X(V) = \mathrm{qf}(X + V)$$
{{% /example %}}

このレトラクションを求める為には例えばシュミットの直交化法などのアルゴリズムを用いる。ちなみに $p=1$ の時は上で例示した $n-1$次元球面のレトラクションと一致する。

---

QR分解ではなく極分解を用いる事もできる。

{{% proposition title="極分解" %}}
$\mathrm{Sym}^+_n$ を$n\times n$正定値実対称行列の集合とする。

任意の $X\in\mathbb{R}^{m\times n}_\ast, (m\geq n)$ は

$$ X=UP\quad (U\in \mathbb{R}^{m\times n}, P\in \mathrm{Sym}^+_n, U^TU=I)$$
と一意に分解でき、
$$
U=X(X^TX)^{-\frac{1}{2}},\quad P=(X^TX)^{-\frac{1}{2}}
$$
である。
{{% /proposition %}}

この分解に対して {{< ref prop.retraction >}} を用いると以下が示せる。

{{% example title="直交群の極分解によるレトラクション" %}}
直交群 $O_n$ の点 $X$ と $V=X\Omega\in T_XO_n$ に対して
$$ R_X(V) = X(I+\Omega)(I-\Omega^2)^{-1/2} $$
{{% /example %}}

$ U = X(X^TX)^{-1/2}$ の $X$ に $X+V=X+X\Omega=X(I+\Omega)$ を代入して
$$\begin{aligned}
\mathrm{R}_X(X\Omega) &= X(I+\Omega)((X(I+\Omega))^TX(I+\Omega))^{-\frac{1}{2}} \\\\
&= X(I+\Omega)((I-\Omega)X^TX(I+\Omega))^{-\frac{1}{2}} \\\\
&= X(I+\Omega)(I-\Omega^2)^{-\frac{1}{2}} \quad(\because X^TX=I)\\\\
\end{aligned}$$

直交群の場合はQR分解に比べると計算量が多くあまり有用な場面はない。

{{% example title="シュティーフェル多様体の極分解によるレトラクション" %}}
シュティーフェル多様体 $\mathrm{St}(p,n)$ の点 $X$ と $V=T_X\mathrm{St}(p,n)$ に対して
$$ R_X(V) = (X+V)(I+V^TV)^{-\frac{1}{2}} $$
{{% /example %}}

$$ T_X\mathrm{St}(p,n)=\\{Z\in\mathbb{R}^{n\times p}\mid Z^TX+X^TZ=0\\}$$ 
であたので
$ U = X(X^TX)^{-1/2}$ の $X$ に $X+V$ を代入して
$$\begin{aligned}
\mathrm{R}_X() &= (X+V)((X+V)^T(X+V))^{-\frac{1}{2}} \\\\
&= (X+V)(X^TX + V^TV + V^TX+X^TV)^{-\frac{1}{2}} \\\\
&= (X+V)(I + V^TV)^{-\frac{1}{2}} \quad(\because X^TX=I,V^TX+X^TV=0)\\\\
\end{aligned}$$

{{% example title="直交群のCayley変換によるレトラクション" %}}
直交群 $O_n$ の点 $X$ と $V=X\Omega\in T_XO_n$ に対して
$$ \mathrm{R}_X(V)=X\left(I-\frac{1}{2}\Omega\right)^{-1}\left(I+\frac{1}{2}\Omega\right) $$
{{% /proposition %}}

{{% example title="直交群のGivens回転によるレトラクション" %}}
単位行列の $(i,i)$成分と$(j,j)$成分を $\cos\theta$に、 $(i,j)$成分と$(j,i)$成分を$\sin\theta$ と $-\sin\theta$ に置き換えたものを **ギブンズ回転(Givens rotation)** という。これは $ij$平面での回転を表す。
$$G(i,j,\theta)=\begin{pmatrix}
1 & \cdots & 0 & \cdots & 0 & \cdots & 0 \\\\
\vdots & \ddots & \vdots &   & \vdots &  & \vdots \\\\
0 & \cdots & \cos\theta & \cdots & \sin\theta & \cdots & 0 \\\\
\vdots &  & \vdots & \ddots & \vdots &  & \vdots \\\\
0 & \cdots & -\sin\theta & \cdots & \cos\theta & \cdots & 0 \\\\
\vdots &  & \vdots & & \vdots & \ddots & \vdots \\\\
0 & \cdots & 0 & \cdots & 0 & \cdots & 1 \\\\
\end{pmatrix}$$

直交群 $O_n$ の点 $X$ と $V=X\Omega\in T_XO_n$ に対して
$$\mathrm{R}_X(V)=X\mathrm{Giv}(\Omega)=\prod\_{i<j}G(i,j,\Omega\_{ij})$$
{{% /proposition %}}

{{% example title="直交群の指数写像によるレトラクション" %}}
直交群 $O_n$ の点 $X$ と $V=X\Omega\in T_XO_n$ に対して
$$\mathrm{R}_X(V)=X\exp\Omega = X\sum\_{k=0}^\infty\frac{1}{k!}\Omega^k$$
{{% /example %}}

続いて商多様体のレトラクションの構成方法について。

{{% proposition %}}
$\mathcal{M}$ を多様体 $\mathcal{M}/{\sim}$ をその商多様体、 $\pi:\mathcal{M}\rightarrow\mathcal{M}/{\sim}$ を自然な全射とする。

$\mathrm{R}:T\mathcal{M}\rightarrow\mathcal{M}$ を$\mathcal{M}$ のレトラクションであり、任意の
$v\in T_{[x]}\mathcal{M}/{\sim}$ とその点 $a,b\ ([a]=[b]=[x])$ への水平リフト $v_a,v_b$ に対して
$$ \pi(\mathrm{R}_a(v_a)) = \pi(\mathrm{R}_b(v_b)) $$
となるようなものであるならば、

$$ \mathrm{R}'_{[x]}(v) := \pi(\mathrm{R}_x(v_x)) $$

は代表元 $x$ の選び方によらずwell-definedであり、 $\mathcal{M}/{\sim}$ のレトラクションとなる。
{{% /proposition %}}

{{% example title="実射影空間のレトラクション" %}}
実射影空間 $\mathbb{RP}^{n-1}=\mathbb{R}^n\_\ast/\mathbb{R}\_\ast$ の点 $[x]$ とベクトル $v\in T_{[x]}\mathbb{RP}^{n-1}$ について、 $v$ の点 $x$ での水平リフトを $v_x$ とすると
$$\mathrm{R}_{[x]}(v) = \pi(x + v_x)$$
はレトラクション。ただし $\pi:\mathbb{R}^n\_\ast\rightarrow\mathbb{RP}^{n-1}$ は自然な全射。
{{% /example %}}

$x\sim y$ とすると $y=\alpha x\quad(\alpha\in\mathbb{R}\_\ast)$ と表す事ができる。この時 $v_{\alpha x}=\alpha v_x$ であったから

$$ \mathrm{R}\_{[y]}(v)=\pi(y+v_y)=\pi(\alpha x + \alpha v_x) = \pi (x + v_x) = \mathrm{R}_{[x]}(v) $$

これはwell-defined。その他の条件については省略する。 $\square$

グラスマン多様体についても同様。

{{% example title="グラスマン多様体のレトラクション" %}}
グラスマン多様体 $\mathrm{Grass}(p,n)=\mathbb{R}^{n\times p}\_\ast/\mathrm{GL}_p$ の点 $[X]$とベクトル $V\in T\mathrm{Grass}(p,n)$ について $V$ の $X$ での水平リフトを $V_X$ とすると
$$ \mathrm{R}\_{[X]}(V)=\mathrm{span}(X+V_X) $$
はレトラクション。ただし $\mathrm{span}:\mathbb{R}^{n\times p}\_\ast\rightarrow\mathrm{Grass}(p,n)$ は自然な全射。
{{% /example %}}

レトラクションの重要な性質として以下が成り立つ。つまり、 $\mathcal{M}$ 上での勾配を、ベクトル空間 $T_x\mathcal{M}$ の勾配として求める事が可能になる。

{{% proposition %}}
$\mathcal{M}$ がリーマン多様体である時、
滑らかな関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ とレトラクション $R:T\mathcal{M}\rightarrow\mathcal{M}$ について
$$ \mathrm{grad}(f\circ R_x)(0) = \mathrm{grad} f(x) $$
{{% /proposition %}}

