---
title: 7. リーマン多様体
section: 7
---

前節までで多様体上で定義された滑らかな関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ の方向微分は計算できるようになったが、最適化アルゴリズムを実行する為には **勾配(gradient)** が必要である。そして、勾配を定義する為には多様体に **リーマン計量(Riemannian metric)** という構造を入れる必要がある。

勾配を定めるのに何故リーマン軽量が必要なのか戸惑うかもしれない(私は最初は戸惑った)。接ベクトル空間 $T_x\mathcal{M}$ を定めることができて各接ベクトル $v\in T_x\mathcal{M}$ に沿った方向微分を計算できるのに、何故勾配を定める事ができないのか？という事である。

そもそも勾配とはなんであるかというと、ベクトル解析における概念では $f$ の変化率が最大となる方向を向いていて、ノルムがその変化率であるようなベクトル指すのだった。多様体の上での勾配はこれを一般化した概念としたいが、接ベクトル $v\in T_x\mathcal{M}$ の **長さ** が与えられていないので、変化率が最大つまり **同じ距離だけ進んだ時** に $f$ が最も大きく変化する方向を定める事ができない。リーマン計量を入れれば、ベクトルの長さなどの幾何学的性質を多様体の上で定義する事が可能になる為、勾配も定義する事が可能になる。

---

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

また $g_x(u,v)$ の代わりに $\langle u, v\rangle _x$ や、$x$ を省略して $\langle u,v\rangle$ と書く。

さて、内積が定まったのでベクトル $u\in T_x\mathcal{M}$ に対して、そのノルムを定める事が出来る。

{{% definition title="ノルム" %}}
$$ ||u|| = \sqrt{\langle u, u\rangle} $$
をベクトル $u$ の **ノルム(norm)** という。
{{% /definition %}}

あるチャートを選ぶと、接ベクトルは基底
$$ \left(\frac{\partial}{\partial x_i}\right)_x$$ 
で成分表示できるので、リーマン計量 $g_x$ は行列 $G_x$ 

$$ (G_x)_{ij} := \left\langle \left(\frac{\partial}{\partial x_i}\right)_x,\left(\frac{\partial}{\partial x_j}\right)_x \right\rangle $$

によって定まる。これが内積を定める必要十分条件は $G_x$ が正定値対称行列である事である。接ベクトル $u,v\in T_x\mathcal{M}$ の標準基底に対する成分を $\mathbf{u},\mathbf{v}\in\mathbb{R}^m$ とすれば

$$\langle u, v \rangle = \mathbf{u}^TG_x\mathbf{v} $$

となる。

このようにリーマン計量は正定値対称行列を用いて簡単に定める事が出来るが、あくまで一つのチャートの中についてだけであって $\mathcal{M}$ 全体についての計量になっていないので注意。ここで、以下の命題が成り立つ。

{{% proposition %}}
(第二可算でハウスドルフな)多様体 $\mathcal{M}$ には少なくとも一つのリーマン計量を定める事が出来る。
{{% /proposition %}}

第二可算性が嬉しい命題がここで登場した。


$\mathcal{M}$ が第二可算かつハウスドルフならば **1の分割(partition of unity)** というものが存在する事が示せて、これを使って任意の多様体にリーマン計量を定める事が出来る。詳しい証明を書くのは重たい上、本筋から外れてしまうが、気持ちを説明する。

まず $\mathcal{M}$ の適当なアトラス $\mathcal{A}=\\{(U_\alpha,\varphi_\alpha)\\}$ を取ると、上で示したように各チャートの中ではリーマン計量の存在を示す事が簡単に出来る。例えば

$$ G_x = I_m $$

とすれば良い。

問題はチャートとチャートが重なっている部分である。そこで、1の分割というものを利用してチャートが重なっている部分の計量をブレンドしていく。1の分割というのはこのブレンドの為の重み付けを表す関数族のこと。具体的には、各チャート $U_\alpha$ に備え付けられた滑らかな関数 $\rho_\alpha:U_\alpha\rightarrow[0,1]$ であって、 $U_\alpha$ の外では $\rho_\alpha(x)=0$ になり、各点 $x$ について $\rho_\alpha(x) > 0$ となるものは有限個しかなく、全ての点で $\sum_\alpha \rho_\alpha(x) = 1$ となるようなもの。
