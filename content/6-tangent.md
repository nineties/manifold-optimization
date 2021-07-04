---
title: 6. 接ベクトル空間
section: 6
---

多様体上でニュートン法などの最適化アルゴリズムを実行する為には、点 $x\in\mathcal{M}$ で勾配や方向微分に相当するものを計算できる必要がある。多様体 $\mathcal{M}$ 上の実数値関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ の点 $x\in\mathcal{M}$ での方向 $\eta$ についての方向微分は、多様体上の点について加法が定義されていないので

$$ \mathrm{D}\_{f}(x)[\eta] = \lim_{t\rightarrow 0}\frac{f(x+t\eta)-f(x)}{t} $$

といった感じでは書けない。方向 $\eta$ をどう表現するかも明らかではない。チャートを使うというのが一つの方法だが、そうするとチャートの選び方に依存したものとなり使い勝手が悪い。そこで、接ベクトルや接ベクトル空間といった概念が登場する。

接ベクトルの定義にはいくつかの流儀があるみたいで、今回参考にしている[教科書](https://press.princeton.edu/absil)では多様体上の実関数に対する微分作用素を接ベクトルとする定義を採用している。この定義は理屈としては分かるものの、図形的な直感を(私は)なかなか得られなかったので、このノートでは別の定義から出発したいと思う。 そちらの定義では曲線の同値類として接ベクトルを定義をする。

---

滑らかな写像 $\gamma:(-\varepsilon,\varepsilon)\rightarrow\mathcal{M}$ を $\mathcal{M}$ 上の **曲線(curve)** という。(曲線の定義域は開集合であればなんでも良いが、今は $t=0$ 付近にしか興味がないのでこう書く事にする。)

{{< figure src="../images/curve.png" >}}

点 $x$ を通る曲線を用いる事で $x$ における点の運動を表現できそうである。但し、関心があるのは $x$ の局所的な様子であって曲線全体ではないので、 $x$ において同じ運動をしていると見なせる曲線群を同一視しようというのがこの定義のアイデアである。同じ運動をしているか否かは、点 $x$ の周囲に座標系を貼り付けた時に同じ速度ベクトルになっているか否かで判断できる。

{{% definition title="接ベクトル" %}}
$t=0$ で点 $x\in\mathcal{M}$ を通る曲線の集合
$$ \mathcal{L}_x = \\{\gamma:(-\varepsilon,\varepsilon)\rightarrow\mathcal{M} \mid \gamma(0)=x \\}$$
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

---

以上のような曲線の同値類としての接ベクトルの定義は直感的に理解しやすいが、これと微分作用素としての定義がどう関係するのか説明する。

{{% definition title="方向微分" %}}
多様体 $\mathcal{M}$ 上で定義された滑らかな関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ と
点 $x\in\mathcal{M}$ を通る曲線 $\gamma:\mathbb{R}\rightarrow\mathcal{M},\gamma(0)=x$ について

$$
\frac{\mathrm{d}(f\circ\gamma)}{\mathrm{d}t}(0)
$$

を $f$ の点 $x$ における曲線 $\gamma$ に沿った **方向微分(directional derivative)** という。
{{% /definition %}}

そして、以下が成り立つ。

{{% proposition %}}
$x\in\mathcal{M}$ を通る曲線 $\gamma_1,\gamma_2$ について $\gamma_1\sim\gamma_2$ であるならば、任意の滑らかな関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ に対して、点 $x$ における$\gamma_1,\gamma_2$ に沿った方向微分は一致する。
{{% /proposition %}}

$$
\frac{\mathrm{d}(f\circ\gamma)}{\mathrm{d}t}(0) = J_{f\circ\varphi^{-1}}(\varphi(x))\frac{\mathrm{d}(\varphi\circ\gamma)}{\mathrm{d}t}(0)
$$

より $\square$

$x$ で滑らかな実数値関数 $\mathcal{M}\rightarrow\mathbb{R}$ の集合を $C_x(\mathcal{M})$ とし、点 $x$ を通る曲線の同値類 $[\gamma]$ に対して、方向微分を返す関数

$$ v_{[\gamma]}:C_x(\mathcal{M})\rightarrow\mathbb{R}: f \mapsto
\frac{\mathrm{d}(f\circ\gamma)}{\mathrm{d}t}(0) $$

を考える。これらの集合を $T'_x\mathcal{M}$ とおくと $T_x\mathcal{M}$ と $T'_x\mathcal{M}$ の間には全単射が存在する。対応$[\gamma]\mapsto v\_{[\gamma]}$ を考えると、これは代表元の選び方によらず単射となる。また、$v\in T'_x\mathcal{M}$ が与えられたら、 $x$ の周りのチャート $(U,\varphi)$ に対して曲線の同値類

$$\phi^{-1}(v(\varphi_1),\ldots,v(\varphi_m))$$

が存在するので全射である。

$T'_x\mathcal{M}$ にも加算とスカラー倍を以下のように定義する事が出来る。$u,v:T'_x\mathcal{M}, a,b\in\mathbb{R}$ に対して

$$ (au+bv)(f) = au(f) + bv(f)$$

すると $T_x\mathcal{M}$ と $T'_x\mathcal{M}$ はベクトル空間として同型になる

$$ T_x\mathcal{M} \simeq T'_x\mathcal{M} $$

細かな証明は省略するが、方向微分を成分表示してみると、 $(x_1,\ldots,x_m)=(\varphi_1(x),\ldots,\varphi_m(x))$ とおいたとき

$$
\frac{\mathrm{d}(f\circ\gamma)}{\mathrm{d}t}(0) = \sum_i\frac{\mathrm{d}(\varphi_i\circ\gamma)}{\mathrm{d}t}(0)\left(\frac{\partial (f\circ\varphi^{-1})}{\partial x_i}\right)_x 
$$

となる。これと曲線の同値類の成分表示

$$[\gamma] = \sum_i\frac{d(\varphi_i\circ\gamma)}{\mathrm{d}t}(0)\phi^{-1}(e_i) $$

を見比べると、標準基底 $e_i$ に対応する基底は、こちらでは微分作用素

$$ f \longmapsto \left(\frac{\partial (f\circ\varphi^{-1})}{\partial x_i}\right)_x $$

になって、 $x_i$ 軸方向の偏微分操作を表しているという事が分かる。そして、同じチャートを利用したときにベクトルの成分が2つの定義で全く同じになるということも分かる。

$f$ が最初から $\mathbb{R}^m$ 上の関数であるならば、接ベクトル空間の基底は

$$\left(\frac{\partial}{\partial x_i}\right)_x$$

とシンプルに表される。

以上のように接ベクトル空間には複数の同型な定義の仕方がある。今後文脈から明らかな場合には同じ記号 $T_x\mathcal{M}$ を利用する。

{{% definition title="接バンドル" %}}
接空間の全ての点での直和
$$ T\mathcal{M} = \bigsqcup\_{x\in\mathcal{M}} T_x\mathcal{M} $$
を $\mathcal{M}$ の **接バンドル(tangent bundle)** という。
{{% /definition %}}

$\dim\mathcal{M}=n$の時、接バンドル $T\mathcal{M}$ は $2n$ 次元多様体見なすことが出来る。というのは $\mathcal{M}$ の$x$の周りのチャート $(U,\varphi)$ に対して

$$ \varphi': T_x\mathcal{M}\rightarrow\mathbb{R}^{2m}: v\mapsto (\varphi_1(x),\ldots,\varphi_m(x),v(\varphi_1(x)),\ldots,v(\varphi_m(x)))^T$$

が $T\mathcal{M}$ のチャートとなり、これらを全て集めて $T\mathcal{M}$ のアトラスを構成する事が出来るから。

---

以上で定義された接ベクトル空間と、馴染みのある接線や接平面といったものがどのように関係するかを調べる。もちろん、後者は曲線の同値類や微分作用素ではないので、接ベクトル空間そのものではないが、ベクトル空間として同型である事を示す事が出来る。

{{% proposition %}}
ベクトル空間 $V$ の接ベクトル空間は $V$ と同型
$$ T_xV\simeq V$$
{{% /proposition %}}

直線の接線はその直線自身だし、平面の接平面はその平面自身。実際に計算すると
$v\in T_x V, f\in C_x(V)$ に対して

$$ v(f) = \frac{\mathrm{d}(f\circ\gamma)}{\mathrm{d}t}(0) = \mathrm{D}_{f}(x)\left[\frac{\mathrm{d}\gamma}{\mathrm{d}t}(0)\right]=\mathrm{D}\_{f}(x)[\dot{\gamma}(0)]$$

となる。($\because$ ベクトル空間であるので $\gamma$ の時間での微分が直接計算できる)

$\mathrm{D}\_{f}(x)$ は曲線 $\gamma$ に依存しないので $v$ と $\dot{\gamma}(0)$ が一対一に対応する。さらに$\mathrm{D}\_{f}(x)$ は線形写像であったから

$$a_1v_1(f)+a_2v_2(f) = \mathrm{D}_{f}(x)[a_1\dot{\gamma_1}(0)+a_2\dot{\gamma_2}(0)]$$

となるので

$$a_1v_1 + a_2v_2 \longmapsto a_1\dot{\gamma_1}(0)+a_2\dot{\gamma_2}(0)$$

という綺麗な対応が得られる。

---

$\mathcal{M}$ がベクトル空間 $V$ の部分多様体である場合も $V$ の中で同じように $\dot{\gamma}(0)$ を計算する事ができて、接ベクトル空間は馴染みのある接空間と(ベクトル空間の同型として)一致する。つまり

$$ T_x\mathcal{M} \simeq \\{\dot{\gamma}(0)\mid \gamma:(-\varepsilon,\varepsilon)\rightarrow\mathcal{M},\gamma(0)=x\\}$$

{{% example title="$n$次元球面" %}}
$$S^n = \\{x\in\mathbb{R}^{n+1}\mid||x||=1\\}$$
の接ベクトル空間は
$$T_xS^n=\\{z\in\mathbb{R}^{n+1}\mid x^Tz=0\\}$$
{{% /example %}}

任意の $S^n$ 上の曲線 $t\mapsto x(t)$ について
$ ||x||^2 = 1 $ より $\dot{x}(t)^Tx(t) = 0$ となる事から。

{{% example title="コンパクトシュティーフェル多様体" %}}
$$\mathrm{St}(p,n)=\\{X\in\mathbb{R}^{n\times p}\mid X^TX = I_p\\}\quad(p\leq n)$$
の接ベクトル空間は

$$ T_X\mathrm{St}(p,n) = \\{Z\in\mathbb{R}^{n\times p}\mid Z^TX+X^TZ=0\\} $$
{{% /example %}}

$X(t)^TX(t)=I_p$ を $t$ で微分する事によって得られる。

{{% example title="直交群" %}}
$$ O_n = \\{X\in\mathbb{R}^{n\times n}\mid X^TX=I \\\}$$
の接ベクトル空間は
$$ T_xO_n = \\{ X\Omega\mid \Omega^T=-\Omega \\} $$
{{% /example %}}

$X\in O_n$ は正則行列だから、適当な行列 $\Omega$ が存在して
$\dot{X} = X\Omega$ と書ける。ここで $X^TX=I$ より
$\dot{X}^TX+X^T\dot{X}=0$ だから
$$\Omega^TX^TX+X^TX\Omega=0 \Rightarrow \Omega^T + \Omega = 0$$
