---
title: 10. 直線探索
section: 10
---


続いて、レトラクションを用いた直線探索の更新式

$$ x_{k+1} = R_{x_k}(t_kv_k) $$

の **探索方向(search direction)** $v_k$ と、 **ステップサイズ(step size)** $t_k$ をどのように選ぶべきかについて調べる。
これらは反復法が収束する事や収束先が停留点であるといった性質を持つように選ぶ必要がある。

ところで、多様体上の点列が収束するとはそもそもどういう事かというところから確認していく。

{{% definition title="点列の収束(チャートを用いた定義)" %}}
多様体 $\mathcal{M}$ 上の点列 $\\{x_k\\}$ に対して、あるチャート $(U,\psi)$ と点 $x\_{\ast} \in U$ が存在し、ある自然数 $K$ について
$k > K$ ならば $x_k \in U$ であり、$\psi(x_k)$ が $\psi(x\_\ast)$ に収束するならば、 $\\{x_k\\}$ は **収束する (convergent)** という。
また、
$$ \psi^{-1}(\lim\_{k\rightarrow\infty} \psi(x_k)) $$
を $\\{x_k\\}$ の **極限(limit)** といい、 $\lim_{k\rightarrow\infty}x_k$ と書く。

また $\\{x_k\\}$ の適当な部分列が $x\in\mathcal{M}$ に収束するならば $x$ をこの点列の **極限点(limit point)** と呼び、 $\\{x_k\\}$ の極限点の集合を **極限集合(limit set)** という。
{{% /definition %}}

つまり適当なチャートの上に移ってユークリッド空間の点列としての極限を取ってから、$\mathcal{M}$ に戻せば良い。
また、多様体は位相空間であるから近傍を用いて点列の極限を定義する事も出来てこれらの定義は同値。
細かい証明は省略するが $\psi$ は同相写像であるからほぼ明らか。

{{% definition title="点列の収束(近傍を用いた定義)" %}}
多様体 $\mathcal{M}$ 上の点列 $\\{x_k\\}$ が点 $x\_\ast$ に収束するとは、任意の $x\_\ast$ の近傍 $U$ に対して十分大きな $K$ を取れば、
$x_{K+1},x_{K+2},\ldots \in U$ となること。
{{% /definition %}}

というわけで、位相空間の極限に関する性質は同じく多様体についても成立。重要なものは以下。

{{% proposition %}}
(ハウスドルフ空間である) 多様体 $\mathcal{M}$ 上の任意の収束する点列についてその極限は一意に定まる。
{{% /proposition %}}

{{% proposition %}}
多様体 $\mathcal{M},\mathcal{N}$ の間の写像 $f:\mathcal{M}\rightarrow\mathcal{N}$ が連続であるならば、任意の収束する$\mathcal{M}$の点列 $\\{x_k\\}$ に対して

$$ \lim_{k\rightarrow\infty} f(x_k) = f\left(\lim_{k\rightarrow\infty} x_k\right) $$

{{% /proposition %}}

探索方向 $v_k$ については $f(x_k)$ の値が減少する方向を選びたいので

$$ \langle\mathrm{grad} f(x_k), v_k)\rangle < 0$$

となるように選べば良い。([Absil本](https://press.princeton.edu/absil)では $\\{x_k\\}$ に対する **Gradient-related sequence** になるように選ぶとあるが、収束性の証明が面倒になる割にそこまで一般化するメリットがあまりないので、このノートではシンプルにする。特にArmijo pointを求めるアルゴリズムはGradient-related sequenceであるだけだと条件が弱くて停止しない場合があると思う。私が間違ってたら教えてください。)

ステップサイズ $t_k$ は以下のArmijo条件を満たすように取ると良い。

{{% definition title="Armijo条件" %}}
リーマン多様体 $\mathcal{M}$、 滑らかな関数 $f:\mathcal{M}\rightarrow\mathbb{R}$、 レトラクション $R:T\mathcal{M}\rightarrow\mathcal{M}$、点 $x\in\mathcal{M}$、接ベクトル $v\in T_x\mathcal{M}$、定数 $c\in (0,1)$ についてステップサイズ $t > 0$ が

$$ f(R_x(t v)) \leq f(x) + c \langle\mathrm{grad}f(x),t v \rangle $$

を満たす時、 $t$ は **Armijo条件(Armijo Condition)** を満たすという。
{{% /definition %}}

Armijo条件は移動 $x\rightarrow R_x(tv)$ によって $f$ の値が十分減少する事を要求する条件であり、求める減少の大きさはパラメータ $c\in(0,1)$ によって制御する。非常に小さな値 (例えば $10^{-4}$)が使われる事が多い。
ユークリッド空間 $\mathbb{R}$ 上の滑らかな関数 $y=f(x)$ に対するArmijo条件を図示すると下図のようになる。(もちろん、一般の多様体に対してこのような図示は難しい。)

{{< figure src="../images/armijo.png" >}}

Armijo条件を満たす $t$ を見つける方法としては、例えば以下のアルゴリズムがある。
(下記アルゴリズムで見つかる点をAbsil本ではArmijo Pointと呼んでいる。)

{{% algorithm title="ArmijoのBacktrackingアルゴリズム" %}}

$\alpha > 0$ を十分大きな定数、 $\beta \in (0, 1)$ とする。

1. $t=\alpha$ とする。これがArmijo条件を満たすならば終了する。
2. $t \leftarrow \beta t$ とし1に戻る。

{{% /algorithm %}}

$\alpha=1, \beta=1/2$ といった値がよく使われると思う。
もちろん、 $f(R_x(t v))$ が最も小さくなるような$t\_\ast = \mathrm{argmin}_t f(R_x(t v))$ を厳密に求める事ができるならばそれでも良い。
Backtrackingアルゴリズムは以下の重要な性質を持つ。

{{% theorem %}}
$f(x)$ が停留点でなく、 $\langle\mathrm{grad}f(x),v\rangle < 0$ であるならば、 ArmijoのBacktrackingアルゴリズムは有限ステップで停止する。
{{% /theorem %}}

【証明】背理法により示す。Backtrackingアルゴリズムが停止しないとすると、$n=0,1,2,\ldots$ に対して
$$ f(R_x(\alpha\beta^n v)) > f(x) + c \langle\mathrm{grad}f(x),\alpha\beta^n v \rangle $$
すなわち
$$ \frac{f(R_x(\alpha\beta^n v))-f(R_x(0))}{\beta^n} > c\alpha \langle\mathrm{grad}f(x),v \rangle \quad(\because R_x(0)=x)$$
が成立。ここで $n\rightarrow\infty$ の極限をとると

$$ \left.\frac{\mathrm{d}}{\mathrm{d}t} f(R_x(\alpha t v))\right|_{t=0} \geq c\alpha \langle\mathrm{grad}f(x),v \rangle$$

この左辺は

$$\left.\frac{\mathrm{d}}{\mathrm{d}t} f(R_x(\alpha t v))\right|_{t=0} = \mathrm{D}f(R_x(0))[\mathrm{D}R_x(0)[\alpha v]]=\mathrm{D}f(x)[\alpha v]=\langle\mathrm{grad}f(x),\alpha v\rangle = \alpha\langle\mathrm{grad}f(x),v\rangle$$

であるので

$$ \langle\mathrm{grad}f(x),v\rangle \geq c\langle\mathrm{grad}f(x),v \rangle$$

よって $c\in(0,1)$ より $\langle\mathrm{grad}f(x),v\rangle \geq 0$ となるがこれは矛盾。$\square$

さて、ではいよいよ直線探索のアルゴリズムの説明をする。(Absil本ではいきなり"Accelerated" Line Searchというフレームワークが紹介されるが、本ノートでは単純なものから説明する。)

{{% algorithm title="Line Search (LS)" %}}
リーマン多様体 $\mathcal{M}$、滑らかな関数 $f: \mathcal{M}\rightarrow\mathbb{R}$ 、レトラクション $R:T\mathcal{M}\rightarrow\mathcal{M}$、定数 $c\in (0,1)$とする。

最初の点 $x_0\in\mathcal{M}$ を選び、$k=0,1,2,\ldots$ に対して以下を反復する。

1. 探索方向 $v_k\in T\_{x_k}\mathcal{M}$ を $\langle\mathrm{grad}f(x_k),v_k\rangle<0$ を満たすように選ぶ。
2. Armijo条件を満たすステップサイズ $t_k$ をBacktrackingアルゴリズムにより求める。
3. $x\_{k+1} = R\_{x_k}(t_kv_k)$ とする。

{{% /algorithm %}}
