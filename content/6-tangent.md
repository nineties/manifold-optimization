---
title: 6. 接ベクトル空間
section: 6
---

多様体上でニュートン法などの最適化アルゴリズムを実行する為には、点 $x\in\mathcal{M}$ で勾配や方向微分に相当するものを計算できる必要がある。多様体 $\mathcal{M}$ 上の実数値関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ の点 $x\in\mathcal{M}$ での方向 $\eta$ についての方向微分は、多様体上の点について加法が定義されていないので

$$ \mathrm{D}\_{f}(x)[\eta] = \lim_{t\rightarrow 0}\frac{f(x+t\eta)-f(x)}{t} $$

といった感じでは書けない。方向 $\eta$ をどう表現するかも明らかではない。チャートを使うというのが一つの方法だが、そうするとチャートの選び方に依存したものとなり使い勝手が悪い。そこで、接ベクトルや接ベクトル空間といった概念が登場する。

接ベクトルの定義にはいくつかの流儀があるみたいで、今回参考にしている[教科書](https://press.princeton.edu/absil)では多様体上の実関数に対する微分作用素を接ベクトルとする定義を採用している。この定義は理屈としては分かるものの、図形的な直感を(私は)なかなか得られなかったので、このノートでは別の定義から出発したいと思う。 そちらの定義では曲線の同値類として接ベクトルを定義をする。

---

可微分写像 $\gamma:\mathbb{R}\rightarrow\mathcal{M}$ を $\mathcal{M}$ 上の **曲線(curve)** という。

{{< figure src="../images/curve.png" >}}

点 $x$ を通る曲線を用いる事で $x$ における点の運動を表現できそうである。但し、関心があるのは $x$ の局所的な様子であって曲線全体ではないので、 $x$ において同じ運動をしていると見なせる曲線群を同一視しようというのがこの定義のアイデアである。同じ運動をしているか否かは、点 $x$ の周囲に座標系を貼り付けた時に同じ速度ベクトルになっているか否かで判断できる。

{{% definition title="接ベクトル" %}}
$t=0$ で点 $x\in\mathcal{M}$ を通る曲線の集合
$$ \mathcal{L}_x = \\{\gamma:\mathbb{R}\rightarrow\mathcal{M} \mid \gamma(0)=x \\}$$
の上の同値関係を $x$ を含むチャート $(U,\varphi)$ を用いて
$$
\gamma_1\sim\gamma_2\Longleftrightarrow \frac{\mathrm{d}(\varphi\circ\gamma_1)}{\mathrm{d}t}(0) = \frac{\mathrm{d}(\varphi\circ\gamma_2)}{\mathrm{d}t}(0)
$$
と定める。これはチャートの選び方に寄らない。
$\mathcal{L}_x/{\sim}$ の元を $\mathcal{M}$ の点 $x$ での **接ベクトル(tangent vector)** という。
{{% /definition %}}

ここで定めた商集合 $\mathcal{L}_x/{\sim}$ にはベクトル空間の構造を入れることができる。点 $x$ の周りのチャート $(U,\varphi)$ を固定すると、$\mathcal{M}$ の接ベクトルと $\mathbb{R}^m$ の速度ベクトルが以下の対応によって一対一に対応する。

$$\phi:\mathcal{L}_x/{\sim}\longrightarrow\mathbb{R}^m: [\gamma] \longmapsto \frac{\mathrm{d}(\varphi\circ\gamma)}{\mathrm{d}t}(0) $$

これが単射であるのは定義より明らかで、全射であるのは任意の $v\in\mathbb{R}^m$ に対して

$$ \gamma(t) = \varphi^{-1}(\varphi(x) + vt) $$

とおけば $\phi([\gamma])=v$ となる事から分かる。

接ベクトルの和とスカラー倍と和も対応

$$ a_1[\gamma_1] + a_2[\gamma_2] \longmapsto a_1\frac{\mathrm{d}(\varphi\circ\gamma_1)}{\mathrm{d}t}(0) + a_2\frac{\mathrm{d}(\varphi\circ\gamma_2)}{\mathrm{d}t}(0)$$

によって定めれば良い。具体的に式で書くならば $\phi$ を使って

$$ a_1[\gamma_1] + a_2[\gamma_2] = \phi^{-1}(a_1\phi([\gamma_1])+a_2([\gamma_2])) $$

とすれば良い。これがチャート $(U,\varphi)$ の選び方に依存しない事は簡単に示すことができる。以上より$\mathcal{L}_x/{\sim}$ は$\mathcal{M}$と次元の等しいベクトル空間になる事が分かる。


{{% definition title="接ベクトル空間" %}}
$m$ 次元多様体の点 $x$ における接ベクトルの集合は $m$ 次元ベクトル空間である。これを **接ベクトル空間(tangent vector space)** といい $T_x\mathcal{M}$ と書く。
{{% /definition %}}

ベクトル空間であるからには、基底が存在してその線形結合で任意の元を表す事ができる。
例えば $\mathbb{R}^m$ の標準基底

$$e_i=(0,\ldots,0,1,0,\ldots,0)^T$$

に対応する $T_x\mathcal{M}$ の元 $\phi^{-1}(e_i)$ が基底になる。この時の成分表示は
$\varphi(x)=(\varphi_1(x)\ \cdots\ \varphi_m(x))^T$
と表すと

$$\frac{\mathrm{d}(\varphi\circ\gamma)}{\mathrm{d}t}(0) = \left(\frac{\mathrm{d}(\varphi_1\circ\gamma)}{\mathrm{d}t}(0)\ \cdots\ \frac{\mathrm{d}(\varphi_m\circ\gamma)}{\mathrm{d}t}(0)\right)^T=\sum_{i}\frac{\mathrm{d}(\varphi_i\circ\gamma)}{\mathrm{d}t}(0)e_i$$

なので、$\phi^{-1}$ で $T_x\mathcal{M}$ に移すと

$$[\gamma] = \sum_i\frac{d(\varphi_i\circ\gamma)}{\mathrm{d}t}(0)\phi^{-1}(e_i) $$

となる。
