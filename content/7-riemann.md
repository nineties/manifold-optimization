---
title: 7. リーマン多様体
section: 7
---

前節までで多様体上で定義された滑らかな関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ の方向微分は計算できるようになったが、最適化アルゴリズムを実行する為には **勾配(gradient)** が必要である。そして、勾配を定義する為には多様体に **リーマン計量(Riemannian metric)** という構造を入れる必要がある。

勾配を定めるのに何故リーマン軽量が必要なのか戸惑うかもしれない(私は最初は戸惑った)。接ベクトル空間 $T_x\mathcal{M}$ を定めることができて各接ベクトル $v\in T_x\mathcal{M}$ に沿った方向微分を計算できるのに、何故勾配を定める事ができないのか？という事である。

そもそも勾配とはなんであるかというと、ベクトル解析における概念では $f$ の変化率が最大となる方向を向いていて、ノルムがその変化率であるようなベクトル指すのだった。多様体の上での勾配はこれを一般化した概念としたいが、接ベクトル $v\in T_x\mathcal{M}$ の **長さ** が与えられていないので、変化率が最大つまり **同じ距離だけ進んだ時** に $f$ が最も大きく変化する方向を定める事ができない。リーマン計量を入れれば、ベクトルの長さなどの幾何学的性質を多様体の上で定義する事が可能になり、勾配も定義する事が出来る。

{{% definition title="内積" %}}
実ベクトル空間 $V$ に対して定められた写像 $\langle\cdot ,\cdot\rangle:V\times V\rightarrow\mathbb{R}$
が以下の性質を満たすとき、これを **内積(inner product)** という。

任意の $u,v,w\in V,a\in\mathbb{R}$ に対して

- 対称性: $\langle u,v\rangle = \langle v,u\rangle$
- 第一引数についての線型性: $\langle au+v, w\rangle =a\langle u, w\rangle +\langle v, w\rangle$
- 正定値性: $u\neq 0\Rightarrow \langle u, u\rangle > 0$
{{% /definition %}}

第二引数についての線型性は対称性と第一引数についての線型性より導かれる。
$\langle 0, 0\rangle =\langle 0+0, 0\rangle =\langle 0, 0\rangle + \langle 0, 0\rangle $ より $\langle 0, 0\rangle =0$ なので $\langle u, u\rangle \geq 0$ である事と、非退化性 $\langle u, u\rangle =0\Rightarrow u=0$ も得られる。

{{% definition title="リーマン多様体" %}}
多様体 $\mathcal{M}$ の各点 $x$ の接ベクトル空間に内積
$$g_x:T_x\mathcal{M}\times T_x\mathcal{M}\rightarrow\mathbb{R}$$
が定められており、任意のベクトル場 $U,V$ について写像
$$ \mathcal{M}\ni x\mapsto g_x(U_x,V_x)\in\mathbb{R}$$
が滑らかであるとき、対応 $g:x\mapsto g_x$ を **リーマン計量(Riemannian metric)** という。リーマン計量の備わった多様体 $(\mathcal{M},g)$ を  **リーマン多様体(Riemannian manifold)** という。
{{% /definition %}}

文脈から誤解の恐れがない場合には $g$ を省略して「リーマン多様体 $\mathcal{M}$」と呼ぶ事がある。
