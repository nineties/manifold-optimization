---
title: 9. レトラクション
section: 9
---

各点 $x\in\mathcal{M}$ での勾配が定められるようになったので、次は $\mathcal{M}$ 上で点を動かして最小値を探索する方法を考える。

ユークリッド空間 $\mathbb{R}^n$ の関数 $f:\mathbb{R}^n\rightarrow\mathbb{R}$ に対する **直線探索法(line-search method)** とは点 $x_0\in\mathbb{R}^n$ から出発して、更新式

$$ x_{k+1}=x_k + t_kv_k $$

を反復し $f$ の極小値を求める方法である。ここで $v_k$ は **探索方向(search direction)** と呼ばれるベクトル、 $t_k$ は **ステップサイズ(step size)** と呼ばれるスカラーであって、これらをどのように求めるかによって様々な最適化アルゴリズムが存在する。


多様体 $\mathcal{M}$ 上で同様の探索を行う事を考える。つまり $x_k \in\mathcal{M}$ から $v_k\in T_{x_k}\mathcal{M}$ の方向に探索を進めるということ行いたいわけであるが、 一般の多様体上では直線というものを考えることは出来ないので、

$$
\gamma(0) = x_k,\quad\dot{\gamma}(0)=v_k
$$

を満たす曲線 $\gamma$ に沿って探索を行う。ユークリッド空間での直線探索法と異なり、曲線 $\gamma$ の選び方という自由度が増えている。

{{< figure src="../images/linesearch.png" >}}

このような $\gamma$ は条件さえ満たせばどのように構成しても良いが、レトラクションという接バンドルから多様体への写像を用いるのが一般的である。


{{% definition title="レトラクション" %}}
接バンドル $T\mathcal{M}$ から $\mathcal{M}$ への滑らかな写像 $R:T\mathcal{M}\rightarrow\mathcal{M}$ で以下の条件を満たすものを **レトラクション(retraction)** という。 $R$ の $T_x\mathcal{M}$ への制限を $R_x:T_x\mathcal{M}\rightarrow\mathcal{M}$ と書く。

1. $R_x(0) = x$
2. **局所剛性(local rigidity)** : $\mathrm{D}{R_x}(0)=\mathrm{id}_{T_x\mathcal{M}}$
{{% /definition %}}

イメージとしては下の図のように、接ベクトル空間 $T_x\mathcal{M}$ 上で $x$ から $v$ だけ進んだ点から $\mathcal{M}$ 上に移す写像が $R_x$

{{< figure src="../images/retraction.png" >}}

局所剛性は、任意の $v\in T_x\mathcal{M}$ に対して

$$\mathrm{D}{R_x}(0)[v] = v$$

であるというで、 $x$ の周囲 $(v=0)$ での接ベクトル空間は $R_x$ によって動かないということを言っている。

厳密に言うと、 $\mathrm{D}{R_x}(0)$ は $T_x\mathcal{M}$の接ベクトル空間 $T_0(T_x\mathcal{M})$ から $T_x\mathcal{M}$ への写像
$$ \mathrm{D}{R_x}(0): T_0(T_x\mathcal{M})\rightarrow T_x\mathcal{M} $$
であるが、ベクトル空間の接ベクトル空間はそれ自身と一致するので $T_0T_x\mathcal{M}\simeq T_x\mathcal{M}$ である。つまり微分 $\mathrm{D}{R_x}(0)$ は
$$ \mathrm{D}{R_x}(0): T_x\mathcal{M}\rightarrow T_x\mathcal{M} $$
という写像とみる事が出来て、これが $\mathrm{id}$ であると言うのは接ベクトル空間を動かさないという事に他ならない。

---

さて、レトラクションが与えられると、直線探索を行うのに必要な曲線を以下のようにして構成することができる。


{{% proposition %}}
$R:T\mathcal{M}\rightarrow\mathcal{M}$ をレトラクションとする。接ベクトル $v\in T_x\mathcal{M}$ に対して曲線を
$$ \gamma(t) = R_x(tv) \quad t\in(-\varepsilon,\varepsilon)$$
と定めると
$$ \gamma(0) = x,\ \dot{\gamma}(0) = v $$
{{% /proposition %}}

$\gamma:(-\varepsilon,\varepsilon)\rightarrow\mathcal{M}$ が滑らかな写像であるのは明らかであり $\gamma(0)=R_x(0) = x$ かつ

$$\dot{\gamma}(0) = \mathrm{D}{R_x}(0)\left[\frac{\mathrm{d}(tv)}{\mathrm{d}t}(0)\right] = \mathrm{D}{R_x}(0)[v]=v$$

{{% definition title="レトラクションを用いた探索" %}}

$\mathcal{M}$ を多様体、 $\mathrm{R}$ をレトラクションとする。点 $x_k\in\mathcal{M}$ から接ベクトル $v_k\in T_{x_k}\mathcal{M}$ の方向にステップサイズ $t_k\in\mathbb{R}$ だけ進むことを表す更新式は
$$ x_{k+1} = \mathrm{R}_{x_k}(t_kv_k) $$

{{% /definition %}}

同じ多様体上でも最適化アルゴリズムはレトラクションの選び方によって変化し、効率的に計算できるレトラクションを見つける事が重要となる。
例えばリーマン多様体には **指数写像(exponential mapping)** という自然に定まるレトラクションが存在するが、計算量や数値的安定性の観点から計算機で扱うのは難しい事が多い。数学的な性質の良さと、計算機で実行する上での性質の良さは異なるので注意。

{{% example title="ベクトル空間のレトラクション" %}}
$\mathcal{M}$ がベクトル空間の場合には、通常の直線探索と一致する。

ベクトル空間 $\mathcal{M}$ の点 $x$ と、接ベクトル $v\in T_x\mathcal{M}$ に対して、同型 $\mathcal{M}\simeq T_x\mathcal{M}$ を用いて
$$ R_x(v) = x + v $$
と定めると、これはレトラクションであり、更新式は

$$ x_{k+1} = \mathrm{R}_{x_k}(t_kv_k) = x_k + t_kv_k $$
{{% /example %}}

続いて、$\mathcal{M}$ がベクトル空間 $\mathcal{V}$ の部分多様体である場合を考える。この場合も 点 $x\in\mathcal{M}$ と接ベクトル $v\in T_x\mathcal{M}$ の加算 $ x + v $ を$\mathcal{V}$ の中で求める事が出来る。従って $x+v$ を $\mathcal{M}$ の点に移す写像によってレトラクションを構成する事ができる。

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

下図の様なイメージ。ベクトル空間 $\mathcal{V}$ を2つの多様体 $\mathcal{M},\mathcal{N}$ に分解する写像 $\phi^{-1}$ を考えて、
$\mathcal{V}$ の中で計算した $x + v$ から $\mathcal{M}$ への写像を構成している。

{{< figure src="../images/retraction-by-decomposition.png" >}}

[証明]
$R_x$ が滑らかな写像となるのは明らか。

$$ R_x(0) = \pi(\phi^{-1}(x+0)) = \pi(\phi^{-1}(x)) = \pi(x, e) = x $$

また,任意の $v\in T_x\mathcal{M}$ に対して

$$ \begin{aligned}
  & \mathrm{D}{R\_x}(0)[v] \\\\
= & \mathrm{D}(\pi\circ\phi^{-1})(x)[v] \\\\
= & \mathrm{D}\pi(\phi^{-1}(x))[\mathrm{D}\phi^{-1}(x)[v]] \\\\
= & \mathrm{D}\pi(\phi^{-1}(x))[(v,0)] \\\\
= & \mathrm{D}\pi(x,e)[(v,0)] \\\\
= & v
\end{aligned}$$

$\square$

{{% example title="$n$次元球面のレトラクションの例" %}}
$S^n$ 上の点 $x$ と $v\in T_x S^n$ に対して
$$\mathrm{R}_x(v) = \frac{x+v}{||x+v||} $$
{{% /example %}}

$$\phi:S^n\times\mathbb{R}_+\rightarrow\mathbb{R}^{n+1}\_\ast: (x,r) \mapsto rx $$

とおく。これは$r=1$に固定すると恒等写像になり、

$$ \phi^{-1}(x) = (x/||x||,||x||)$$

であり、{{< ref prop.retraction >}} を使用すると上記レトラクションを得る。

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
であったので
$ U = X(X^TX)^{-1/2}$ の $X$ に $X+V$ を代入して
$$\begin{aligned}
\mathrm{R}_X(V) &= (X+V)((X+V)^T(X+V))^{-\frac{1}{2}} \\\\
&= (X+V)(X^TX + V^TV + V^TX+X^TV)^{-\frac{1}{2}} \\\\
&= (X+V)(I + V^TV)^{-\frac{1}{2}} \quad(\because X^TX=I,V^TX+X^TV=0)\\\\
\end{aligned}$$

---

続いてCayley変換を利用する例。

{{% proposition title="Cayley変換" %}}
任意の $A\in\mathrm{Skew}_n$ に対して $I+A$ は正則であり $(I-A)(I+A)^{-1}$ は直交行列である。

この写像

$$\mathrm{Skew}_n\rightarrow O_n: A\mapsto (I-A)(I+A)^{-1}$$

を **Cayley変換(Cayley Transform)** という。
{{% /proposition %}}


{{% example title="直交群のCayley変換によるレトラクション" %}}
直交群 $O_n$ の点 $X$ と $V=X\Omega\in T_XO_n$ に対して
$$ \mathrm{R}_X(V)=X\left(I-\frac{1}{2}\Omega\right)^{-1}\left(I+\frac{1}{2}\Omega\right) $$
{{% /proposition %}}

これは {{< ref prop.retraction >}} を利用するものではないので、レトラクションの条件を直接示す。
$\mathrm{R}_X$ が滑らかな写像であるのは明らかで$ \mathrm{R}_X(0) = X(I-0)^{-1}(I+0)= X$。
また

$$\mathrm{R}_X(V)=X\left(X-\frac{1}{2}V\right)^{-1}\left(X+\frac{1}{2}V\right) $$

であるので {{< ref prop.derivative-of-multiply >}}と{{< ref prop.derivative-of-inv >}} より

$$
\mathrm{D}\mathrm{R}_X(V)[H]
=\frac{1}{2}X\left(X-\frac{1}{2}V\right)^{-1}H\left(X-\frac{1}{2}V\right)^{-1}\left(X+\frac{1}{2}V\right)
+\frac{1}{2}X\left(X-\frac{1}{2}V\right)^{-1}H
$$
であるので
$$
\mathrm{D}\mathrm{R}_X(0)[H] =\frac{1}{2}XX^{-1}HX^{-1}X +\frac{1}{2}XX^{-1}H = \frac{1}{2}H+\frac{1}{2}H = H
$$
より局所剛性も成立 $\square$


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
$$\mathrm{R}_X(V)=X\mathrm{Giv}(\Omega)=X\prod\_{i<j}G(i,j,\Omega\_{ij})$$
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

