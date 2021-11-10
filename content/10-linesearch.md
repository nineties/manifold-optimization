---
title: 10. 直線探索
section: 10
---


続いて、レトラクションを用いた直線探索の更新式

$$ x_{k+1} = R_{x_k}(t_kv_k) $$

の **探索方向(search direction)** $v_k$ と、 **ステップサイズ(step size)** $t_k$ をどのように選ぶべきかについて調べる。

{{% definition title="Gradient-related sequence" %}}
リーマン多様体 $\mathcal{M}$ 上の滑らかな関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ について、点列 $\\{x_k\\}\,x_k\in\mathcal{M}$ と接ベクトルの列 $\\{d_k\\}\,d_k\in T\_{x_k}\mathcal{M}$ が **gradient-related** であるとは、 $f$ の非停留点に収束する任意の点列 $\\{x_k\\}\_{k\in K}$ について、対応する接ベクトルの列 $\\{d_k\\}\_{k\in K}$ が有界で
$$ \lim\_{N\rightarrow\infty}\sup\_{k\in K,k>N}\langle\mathrm{grad} f(x_k),d_k\rangle < 0$$
が成立する事である。
{{% /definition %}}

(gradient-related sequenceって日本語だと何と呼ばれるのでしょうか？)

$f$ の **停留点** というのは $\mathrm{grad} f(x) = 0$ であるような点 $x$ の事であり、 **非停留点** はそうでない点。接ベクトルの列 $\\{d_k\\}\_{k\in K}$ が有界であるというのは、適当な実数 $M$ が存在して任意の $k\in K$ に対して $||d_k|| < M$ となる事。
