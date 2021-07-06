---
title: 8. 直線探索法
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
2. 局所剛性: $\mathrm{D}\_{R_x}(0)=\mathrm{id}_{T_x\mathcal{M}}$
{{% /definition %}}

$\mathrm{D}\_{R_x}(0)$ は $T_x\mathcal{M}$の接ベクトル空間 $T_0T_x\mathcal{M}$ から $T_x\mathcal{M}$ への写像
$$ \mathrm{D}\_{R_x}(0): T_0T_x\mathcal{M}\rightarrow T_x\mathcal{M} $$
であるが、$T_x\mathcal{M}$ はベクトル空間だから $T_0T_x\mathcal{M}\simeq T_x\mathcal{M}$ であるので
$$ \mathrm{D}\_{R_x}(0): T_x\mathcal{M}\rightarrow T_x\mathcal{M} $$
として上の定義では扱っている。

そして局所剛性は、任意の $v\in T_x\mathcal{M}$ に対して

$$\mathrm{D}\_{R_x}(0)[v] = v$$

であるということ。レトラクションが与えられると、直線探索を行うのに必要な曲線を構成することができる。

{{% proposition %}}
$R:T\mathcal{M}\rightarrow\mathcal{M}$ をレトラクションとする。接ベクトル $v\in T_x\mathcal{M}$ に対して曲線を
$$ \gamma(t) = R_x(tv) \quad (t\in\mathbb{R})$$
と定めると
$$ \gamma(0) = x,\ \dot{\gamma}(0) = v $$
{{% /proposition %}}

$\gamma:\mathbb{R}\rightarrow\mathcal{M}$ が滑らかな写像であるのは明らかであり $\gamma(0)=R_x(0) = x$ かつ

$$\dot{\gamma}(0) = \mathrm{D}_{R_x}(0)\left[\frac{\mathrm{d}(tv)}{\mathrm{d}t}(0)\right] = \mathrm{D}\_{R_x}(0)[v]=v$$

{{< figure src="../images/retraction.png" >}}
