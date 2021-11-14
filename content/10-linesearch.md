---
title: 10. 直線探索
section: 10
---


続いて、レトラクションを用いた直線探索の更新式

$$ x_{k+1} = R_{x_k}(t_kv_k) $$

の **探索方向(search direction)** $v_k$ と、 **ステップサイズ(step size)** $t_k$ をどのように選ぶべきかについて調べる。
これらは反復法が収束する事や収束先が停留点であるといった性質を持つように選ぶ必要がある。

ところで、多様体は位相空間であるので点列の収束は以下のように定義される。

{{% definition title="点列の収束(近傍を用いた定義)" %}}
多様体 $\mathcal{M}$ 上の点列 $\\{x_k\\}$ が点 $x\_\ast$ に **収束する(convergent)** とは、任意の $x\_\ast$ の近傍 $U$ に対して十分大きな $K$ を取れば、
$x\_{K+1},x\_{K+2},\ldots \in U$ となること。

$x\_\ast$ を $\\{x_k\\}$ の **極限(limit)** と呼び$\displaystyle\lim\_{k\rightarrow\infty}x_k$ と書く。
また $\\{x_k\\}$ の無限部分列が $x\in\mathcal{M}$ に収束するならば $x$ をこの点列の **集積点(accumulation point)** と呼び、 $\\{x_k\\}$ の集積点の集合を **極限集合(limit set)** という。
{{% /definition %}}

この定義をチャートを用いて書き直すと以下のようになる。

{{% definition title="点列の収束(チャートを用いた定義)" %}}
多様体 $\mathcal{M}$ 上の点列 $\\{x_k\\}$ が点 $x\_\ast$ に収束するとは、あるチャート $(U,\psi), x\_\ast\in U$ が存在して、十分大きな $K$ を取れば
$x\_{K+1},x\_{K+2},\ldots \in U$ であり、対応するユークリッド空間の点列 $\psi(x\_{K+1}),\psi(x\_{K+2}),\ldots$ が $\psi(x\_\ast)$ に収束すること。
{{% /definition %}}

位相空間の極限に関する性質は同じく多様体についても(もちろん)成立。重要なものは以下。

{{% proposition %}}
(ハウスドルフ空間である) 多様体 $\mathcal{M}$ 上の任意の収束する点列についてその極限は一意に定まる。
{{% /proposition %}}

{{% proposition %}}
多様体 $\mathcal{M},\mathcal{N}$ の間の写像 $f:\mathcal{M}\rightarrow\mathcal{N}$ が連続であるならば、任意の収束する$\mathcal{M}$の点列 $\\{x_k\\}$ に対して

$$ \lim_{k\rightarrow\infty} f(x_k) = f\left(\lim_{k\rightarrow\infty} x_k\right) $$

{{% /proposition %}}

探索方向 $v_k$ は停留点以外では $f(x_k)$ が減少する方向を向いていて欲しい。[Absil本](https://press.princeton.edu/absil)では $\\{x_k\\}$ に対する **Gradient-related sequence** になるように選ぶとあるが、取り扱いが面倒な割にほとんどの場合はここまで一般化する必要がないと思うので、 ここでは以下の条件を満たすように選ぶことにする。
(特に $k$ が小さいところでArmijo pointを求めるアルゴリズムがGradient-related sequenceであるだけだと条件が弱くて停止しない場合があると思う。私が間違ってたらどなたか教えてください。)

{{% definition title="Sufficient descent condition" %}}
探索方向 $v$ はある定数 $\lambda > 0$ が存在して

$$ \langle\mathrm{grad} f(x), v\rangle \leq - \lambda||\mathrm{grad} f(x)||^2$$

が成立し、かつ $||v|| < \infty$ であるように選ぶ。
{{% /definition %}}

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

{{% theorem label="th.backtracking_halts" %}}
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

---

ところで、ユークリッド空間における直線探索ではステップサイズに対して **Wolfe条件(Wolfe condition)** と呼ばれる条件を課す事が多いが、一般の多様体に対してこの条件をそのまま考えることはできない。Wolfe条件というのは、$c' \in (c, 1)$ として

$$ \nabla f(x_k + t_kv_k)^Tv_k\geq \nabla f(x_k)^Tv_k $$

を満たすというもので、これを多様体に一般化すると

$$ \langle \mathrm{grad} f(R_{x_k}(t_kv_k)),v_k\rangle \geq \langle \mathrm{grad}f(x_k),v_k\rangle $$

と書けそうであるが、$\mathrm{grad} f(R_{x_k}(t_kv_k))$ と $v_k$ は同じ接ベクトル空間の元ではないので左辺の内積が定義されない。
Wolfe条件に相当する条件を扱うのは、後に説明するアフィン接続の概念が必要になる。

---

さて、ではいよいよ直線探索のアルゴリズムの説明をする。(Absil本ではいきなり"Accelerated" Line Searchというフレームワークが紹介されるが、本ノートでは単純なものから説明する。)

{{% algorithm title="Backtracking Line Search" %}}
リーマン多様体 $\mathcal{M}$、滑らかな関数 $f: \mathcal{M}\rightarrow\mathbb{R}$ 、レトラクション $R:T\mathcal{M}\rightarrow\mathcal{M}$とする。

最初の点 $x_0\in\mathcal{M}$ を選び、$k=0,1,2,\ldots$ に対して以下を反復する。

1. 探索方向 $v_k\in T\_{x_k}\mathcal{M}$ をSufficient descent conditionを満たすように選ぶ。
2. Armijo条件を満たすステップサイズ $t_k$ をBacktrackingアルゴリズムにより求める。
3. $x\_{k+1} = R\_{x_k}(t_kv_k)$ とする。

{{% /algorithm %}}

{{% theorem %}}
Backtracking Line Searchアルゴリズムの生成する点列 $\\{x_k\\}$ が集積点を持つならばそれは $f$ の停留点である
{{% /theorem %}}

【証明】
Armijo条件と $x_{k+1} = R\_{x_k}(t_kv_k)$ より$ f(x_{k}) \geq f(x_{k+1})$であるので、$\\{f(x_k)\\}$ は $\mathbb{R}$ の単調減少列である。 部分列 $\\{x\_k\\}\_{k\in K}$ が $x\_\ast$ に収束するならば、 $\\{f(x\_k)\\}\_{k\in K}$ は $f(x\_\ast)$ に収束するが $f(x_k)$ が単調減少列であることより $\\{f(x\_k)\\}$ 全体も $f(x\_\ast)$ に収束する。また $f$ は滑らかな関数であるので、 $\\{\mathrm{grad}f(x_k)\\}$ は $\mathrm{grad}f(x_\ast)$ に収束する。

Armijo条件と探索方向の選び方より

$$ f(x_{k+1}) - f(x_k) \leq c t_k\langle\mathrm{grad}f(x_k),v_k \rangle \leq -c\lambda t_k ||\mathrm{grad}f(x_k)||^2 \leq 0 $$

であるが左辺が $k\rightarrow\infty$ で $0$ に収束するので

$$ \lim_{k\rightarrow\infty} t_k||\mathrm{grad}f(x_k)||^2 = 0$$

である。ここで $\mathrm{grad}f(x_\ast) \neq 0$ であるとすると $\lim_{k\rightarrow\infty}t_k=0$ が必要である。
従って、$k$ が十分大きければ$t_k=\alpha\beta^m\,(m\geq 1)$ であり Backtrackingアルゴリズムの1ステップ前のステップサイズ $t_k/\beta$ ではArmijo条件が成立しないから

$$ f\left(R_{x_k}\left(\frac{t_k}{\beta} v_k\right)\right) > f(x_k) + c \frac{t_k}{\beta}\langle\mathrm{grad}f(x_k),v_k \rangle $$

となる。ここで

$$ v'_k = \frac{v_k}{||v_k||},\quad t'_k=\frac{t_k||v_k||}{\beta}$$

とおくと


$$\begin{aligned}
                &\quad f(R_{x_k}(t'_kv'_k)) > f(x_k) + c t'_k\langle\mathrm{grad}f(x_k),v'_k \rangle \\\\
\Leftrightarrow &\quad \frac{f(R_{x_k}(t'_kv'_k))) - f(R_{x_k}(0v'_k))}{t'_k} > c\langle\mathrm{grad}f(x_k),v'_k\rangle
\end{aligned}$$

であるので、中間値の定理よりある $\tilde{t}\in (0,t'_k)$ が存在して

$$\begin{aligned}
                & \quad \left.\frac{\mathrm{d}}{\mathrm{d}t} f(R_{x_k}(tv'_k)\right|_{t=\tilde{t}} > c\langle\mathrm{grad}f(x_k),v'_k\rangle \\\\
\Leftrightarrow & \quad \mathrm{D}f(R_{x_k}(\tilde{t}v'_k))[\mathrm{D}R_x(\tilde{t}v'_k)[v'_k]] > c\langle\mathrm{grad}f(x_k),v'_k\rangle \\\\
\Leftrightarrow & \quad \langle\mathrm{grad}f(x_k),v'_k\rangle > c\langle\mathrm{grad}f(x_k),v'_k\rangle \\\\
\Leftrightarrow & \quad (1-c)\langle\mathrm{grad}f(x_k),v'_k\rangle > 0
\end{aligned}$$
