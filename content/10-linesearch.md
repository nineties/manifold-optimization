---
title: 10. 直線探索
section: 10
---


続いて、レトラクションを用いた直線探索の更新式

$$ x_{k+1} = R_{x_k}(t_kv_k) $$

の **探索方向(search direction)** $v_k$ と、 **ステップサイズ(step size)** $t_k$ をどのように選ぶべきかについて調べる。
これらは反復法が収束する事や収束先が停留点であるといった性質を持つように選ぶ必要がある。

まず、探索方向 $v_k$ はGradient-related sequenceとなるように選ぶと良い。

{{% definition title="Gradient-related sequence" %}}
リーマン多様体 $\mathcal{M}$ 上の滑らかな関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ について、点列 $\\{x_k\\}\,x_k\in\mathcal{M}$ と接ベクトルの列 $\\{v_k\\}\,v_k\in T\_{x_k}\mathcal{M}$ が **gradient-related** であるとは、 $f$ の非停留点に収束する任意の点列 $\\{x_k\\}\_{k\in K}$ について、対応する接ベクトルの列 $\\{v_k\\}\_{k\in K}$ が有界で
$$ \lim\_{N\rightarrow\infty}\sup\_{k\in K,k>N}\langle\mathrm{grad} f(x_k),v_k\rangle < 0$$
が成立する事である。
{{% /definition %}}

(gradient-related sequenceって日本語だと何と呼ばれるのでしょうか？)

$f$ の **停留点** というのは $\mathrm{grad} f(x) = 0$ であるような点 $x$ の事であり、 **非停留点** はそうでない点。接ベクトルの列 $\\{v_k\\}\_{k\in K}$ が有界であるというのは、適当な実数 $M$ が存在して任意の $k\in K$ に対して $||v_k|| < M$ となる事。

また$ \langle\mathrm{grad} f(x_k),v_k\rangle < 0$ であるというのは $v_k$ が $f$ が減少する方向であるという事を表しているので、

$$ \lim\_{N\rightarrow\infty}\sup\_{k\in K,k>N}\langle\mathrm{grad} f(x_k),v_k\rangle < 0$$

であるというのは、最初の方は別として 最終的には $\\{v_k\\}$ が全て $f$ を減少させる方向であるという事。
つまり Gradient-related sequence というのは、停留点以外では(いずれ必ず)減少する方向を向くような方向の列であって、$||v_k||\neq\infty$であるようなもの。

ステップサイズ $t_k$ は以下のArmijo条件を満たすように取ると良い。

{{% definition title="Armijo条件" %}}
リーマン多様体 $\mathcal{M}$、 滑らかな関数 $f:\mathcal{M}\rightarrow\mathbb{R}$、 レトラクション $R:T\mathcal{M}\rightarrow\mathcal{M}$、点 $x\in\mathcal{M}$、接ベクトル $v\in T_x\mathcal{M}$、定数 $c\in (0,1)$ についてステップサイズ $t > 0$ が

$$ f(R_x(t v)) \leq f(x) + c \langle\mathrm{grad}f(x),t v \rangle $$

を満たす時、 $t$ は **Armijo条件(Armijo Condition)** を満たすという。
{{% /definition %}}

Armijo条件は移動 $x\rightarrow R_x(tv)$ によって $f$ の値が十分減少する事を要求する条件であり、求める減少の大きさはパラメータ $c\in(0,1)$ によって制御する。
