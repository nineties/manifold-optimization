---
title: 6. 接ベクトル空間、接バンドル、ベクトル場
section: 6
---

多様体上でニュートン法などの最適化アルゴリズムを実行する為には、点 $x\in\mathcal{M}$ で勾配や方向微分に相当するものを計算できる必要がある。多様体 $\mathcal{M}$ 上の実数値関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ の点 $x\in\mathcal{M}$ での方向 $\eta$ についての方向微分は、多様体上の点について加法が定義されていないので

$$ \mathrm{D}{f}(x)[\eta] = \lim_{t\rightarrow 0}\frac{f(x+t\eta)-f(x)}{t} $$

といった感じでは書けない。方向 $\eta$ をどう表現するかも明らかではない。
適当なチャートを用いれば、ユークリッド空間の関数になるのでこれらを計算する事ができるが、チャートの選び方に結果が依存してしまう為、定義としては使い勝手が良くない。

そこで接ベクトルや接ベクトル空間といった概念が登場するのだが、チャートの選び方に依存しない定義とするために、非常に巧妙なものとなっている。その為とても難しい(と私は感じた)。

接ベクトルの定義にはいくつかの流儀があるみたいで、今回参考にしている[Absil本](https://press.princeton.edu/absil)では多様体上の実関数に対する微分作用素を接ベクトルとする定義を採用している。この定義は理屈としては分かるものの、図形的な直感を(私は)なかなか得られなかったので、このノートでは別のもっと直感的に理解しやすい(と私が思う)定義から出発したいと思う。

---

接ベクトルは多様体上を滑らかに移動する点の速度ベクトルとして理解する事が出来る。

{{% definition title="曲線" %}}
$\varepsilon>0$ の時、滑らかな写像 $\gamma:(-\varepsilon,\varepsilon)\rightarrow\mathcal{M}$ を $\mathcal{M}$ 上の **曲線(curve)** という。
{{% /definition %}}

曲線の定義域は開集合であればなんでも良いが、今は $t=0$ 付近にしか興味がないのでこう書く事にする。

{{< figure src="../images/curve.png" >}}

ここで適当なチャートを選んで $\gamma$ を座標表示すれば、$x=\gamma(0)$ における速度ベクトルを求める事が出来るが、チャートの選び方に依存してしまう。そこで、
**$x$ を通りこの点で同じ運動をしている曲線の集合** を速度ベクトル (接ベクトル) として定める。
同じ運動をしているか否かは、点 $x$ の周囲に座標系を貼り付けた時に同じ速度ベクトルになっているか否かで判断できる。

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

$$\frac{\mathrm{d}(\varphi\circ\gamma_1)}{\mathrm{d}t}(0) = \frac{\mathrm{d}(\varphi\circ\gamma_2)}{\mathrm{d}t}(0)$$

の両辺の速度ベクトルそのものはチャートの選び方によって変わるが、それらが一致するか否かはチャートの選び方には依らないという事である。

$\mathcal{L}_x/{\sim}$ にはベクトル空間の構造を入れることができる。点 $x$ の周りのチャート $(U,\varphi)$ を固定すると、$m$次元多様体 $\mathcal{M}$ の接ベクトルと $\mathbb{R}^m$ の速度ベクトルが以下の対応によって一対一に対応する。

$$\phi:\mathcal{L}_x/{\sim}\longrightarrow\mathbb{R}^m: [\gamma] \longmapsto \frac{\mathrm{d}(\varphi\circ\gamma)}{\mathrm{d}t}(0) $$

これが単射であるのは定義より明らかで、全射であるのは任意の $v\in\mathbb{R}^m$ に対して

$$ \gamma(t) = \varphi^{-1}(\varphi(x) + vt) $$

という曲線を考えると $\phi([\gamma])=v$ となる為。

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
点 $x\in\mathcal{M}$ を通る曲線 $\gamma:(-\varepsilon,\varepsilon)\rightarrow\mathcal{M},\gamma(0)=x$ について

$$
\frac{\mathrm{d}(f\circ\gamma)}{\mathrm{d}t}(0)
$$

を $f$ の点 $x$ における曲線 $\gamma$ に沿った **方向微分(directional derivative)** という。
{{% /definition %}}

($\gamma(t)$ は $\mathcal{M}$ 上の点だったが、 $f\circ\gamma$ は $(-\varepsilon,\varepsilon)\rightarrow\mathbb{R}$ という実数値関数なので $t=0$ での微分係数を通常通り計算する事が出来ることに注意)

そして、以下が成り立つ。

{{% proposition %}}
$x\in\mathcal{M}$ を通る曲線 $\gamma_1,\gamma_2$ について $\gamma_1\sim\gamma_2$ であるならば、任意の滑らかな関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ に対して、点 $x$ における$\gamma_1,\gamma_2$ に沿った方向微分は一致する。
{{% /proposition %}}

$$
\frac{\mathrm{d}(f\circ\gamma)}{\mathrm{d}t}(0) = J_{f\circ\varphi^{-1}}(\varphi(x))\frac{\mathrm{d}(\varphi\circ\gamma)}{\mathrm{d}t}(0)
$$

より $\square$

$x$ で滑らかな実数値関数 $\mathcal{M}\rightarrow\mathbb{R}$ の集合を $C_x(\mathcal{M})$ とし、点 $x$ を通る曲線の同値類 $[\gamma]$ に対して、方向微分を返す関数

$$ \dot{\gamma}(0):C_x(\mathcal{M})\rightarrow\mathbb{R}: f \mapsto
\frac{\mathrm{d}(f\circ\gamma)}{\mathrm{d}t}(0) $$

を考える。これらの集合を $T'_x\mathcal{M}$ とおくと $T_x\mathcal{M}$ と $T'_x\mathcal{M}$ の間には全単射が存在する。対応$[\gamma]\mapsto \dot{\gamma}(0)$ を考えると、上の命題よりこれは代表元の選び方によらずwell-definedであり単射となる。また、$v\in T'_x\mathcal{M}$ が与えられたら、 $x$ の周りのチャート $(U,\varphi)$ に対して曲線の同値類

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

になって、 $x_i$ 軸方向の偏微分操作を表しているという事が分かる。この作用素を

$$\left(\frac{\partial}{\partial x_i}\right)_x$$

とシンプルに表す事がある。

以上のように接ベクトル空間には複数の同型な定義の仕方がある。今後文脈から明らかな場合には同じ記号 $T_x\mathcal{M}$ を利用する。

---

以上で定義された接ベクトル空間と、馴染みのある接線や接平面といったものがどのように関係するかを調べる。もちろん、後者は曲線の同値類や微分作用素ではないので、接ベクトル空間そのものではないが、ベクトル空間として同型である事を示す事が出来る。

{{% proposition %}}
ベクトル空間 $V$ の接ベクトル空間は $V$ と同型
$$ T_xV\simeq V$$
{{% /proposition %}}

直線の接線はその直線自身だし、平面の接平面はその平面自身。実際に計算すると
$v\in T_x V, f\in C_x(V)$ に対して

$$ v(f) = \frac{\mathrm{d}(f\circ\gamma)}{\mathrm{d}t}(0) = \mathrm{D}{f}(x)\left[\frac{\mathrm{d}\gamma}{\mathrm{d}t}(0)\right]=\mathrm{D}{f}(x)[\dot{\gamma}(0)]$$

となる。($\because$ ベクトル空間であるので $\gamma$ の時間での微分が直接計算できる)

$\mathrm{D}{f}(x)$ は曲線 $\gamma$ に依存しないので $v$ と $\dot{\gamma}(0)$ が一対一に対応する。さらに$\mathrm{D}{f}(x)$ は線形写像であったから

$$a_1v_1(f)+a_2v_2(f) = \mathrm{D}{f}(x)[a_1\dot{\gamma_1}(0)+a_2\dot{\gamma_2}(0)]$$

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

{{% example title="シュティーフェル多様体" %}}
$$\mathrm{St}(p,n)=\\{X\in\mathbb{R}^{n\times p}\mid X^TX = I_p\\}\quad(p\leq n)$$
の接ベクトル空間は

$$ T_X\mathrm{St}(p,n) = \\{Z\in\mathbb{R}^{n\times p}\mid Z^TX+X^TZ=0\\} $$

これは $(X\  X_\bot)$ が直交行列となるような $n\times(n-p)$ 行列 $X_\bot$ を用いて以下のようにも書ける。

$$ T_X\mathrm{St}(p,n) = X\mathrm{Skew}\_p + X_\bot\mathbb{R}^{(n-p)\times p} $$
{{% /example %}}

最初の表現は $X(t)^TX(t)=I_p$ を $t$ で微分する事によって得られる。

ここで、 $X$ はフルランクであるから $n\times (n-p)$ 行列 $X_\bot$ で

$$ X^TX_\bot=0,\quad X_\bot^TX_\bot = I_{n-p} $$

となるようなもの、すなわち $X^TX=I_p$ と合わせて $(X\ X_\bot)$ が直交行列となるようなものが存在する。よって、適当な $n\times p$ 行列 $P$ が存在して

$$ \dot{X} = (X\ X_\bot) P $$

と表せる。ここで $P$ を $p\times p$ 行列 $\Omega$ と $(n-p)\times p$ 行列 $K$ によってブロック化する事で


$$ \dot{X} = (X\ X_\bot) \begin{pmatrix} \Omega \\\\ K \end{pmatrix} = X\Omega + X_\bot K $$

と表せる。これを $\dot{X}^TX + X^T\dot{X}=0$ に代入して

$$ (X\Omega + X_\bot K)^TX + X^T(X\Omega + X_\bot K) = \Omega^T+\Omega = 0$$

という条件を得る。次元について確認すると $\Omega$ は$p\times p$歪対称行列なので独立な成分の数は $p(p-1)/2$、 $K$は任意の $(n-p)\times p$ 行列なので、ベクトル空間としての次元は

$$p(n-p)+p(p-1)/2 = np - p(p+1)/2$$

となり、確かに $\mathrm{St}(p,n)$ の次元と一致する。

{{% example title="直交群" %}}
$$ O_n = \\{X\in\mathbb{R}^{n\times n}\mid X^TX=I \\\}$$
の接ベクトル空間は
$$ T_XO_n = X\mathrm{Skew}_n $$
{{% /example %}}

$O_n = \mathrm{St}(n,n)$ より。

---

商多様体 $\mathcal{M}/{\sim}$ 上の接ベクトル空間について考える。多くのケースで $\mathcal{M}/{\sim}$ を直接取り扱うことは難しいので、 $\mathcal{M}$ の接ベクトルと自然な全射 $\pi:\mathcal{M}\rightarrow\mathcal{M}/{\sim}$ を道具として用いて $\mathcal{M}/{\sim}$ の接ベクトルを表したい。具体的には $\pi$ は滑らかな沈め込み写像であるので、任意の接ベクトル $v\in T_{[x]}(\mathcal{M}/{\sim})$ に対して

$$\mathrm{D}{\pi}(x)[u] = v$$

となるような $u$ が存在する(一意ではない)。このような $u$ を $v$ の点 $x$ での **リフト(lift)** というが、これを用いて $\mathcal{M}/{\sim}$ 上の滑らかな関数の方向微分を計算する事が出来る。すなわち、滑らかな関数 $f:\mathcal{M}/{\sim}\rightarrow\mathbb{R}$ に対して

$$ \mathrm{D}{f\circ\pi}(x)[u]=\mathrm{D}f(\pi(x))\left[\mathrm{D}\pi(x)[u]\right] = \mathrm{D}f([x])[v]$$

となる。

このようなリフト $u$ は大量に存在するが、射影 $\pi$ によって消えてしまう成分とそうでない成分に分解する事が出来る。
$\dim\mathcal{M}=m,\dim(\mathcal{M}/{\sim})=n$ とする。
{{< ref th.submersion-theorem >}} より $\pi^{-1}([x])$ は $\mathcal{M}$ の $m-n$次元部分多様体である。よってこれの点 $x$ での接ベクトル空間

$$\mathcal{V}_x = T_x(\pi^{-1}([x]))$$

も $m-n$ 次元のベクトル空間。ここで $T_x\mathcal{M}$ は $m$ 次元のベクトル空間であるので $n$ 次元の $\mathcal{V}_x$ の補空間 $\mathcal{H}_x$ によって

$$ T_x\mathcal{M} = \mathcal{V}_x\oplus\mathcal{H}_x $$

と分解する事が出来る($\mathcal{V}_x\cap\mathcal{H}_x=\\{0\\},\mathcal{V}_x\cup\mathcal{H}_x=T_x\mathcal{M}$)。 $\mathcal{V}_x$ を **垂直空間(vertical space)**、 $\mathcal{H}_x$ を **水平空間(horizontal space)** という。

{{< figure src="../images/horizontal-space.png" >}}

任意の接ベクトル $u\in T_x\mathcal{M}$ はこの分解に基づいて

$$ u=u_V + u_H \quad u_V\in\mathcal{V}_x,u_H\in\mathcal{H}_x$$

と一意的に分解できるが、垂直な成分の方は

$$\mathrm{D}\pi(x)[u_V] = 0$$

と $0$ につぶれてしまう。何故ならば $\pi^{-1}([x])$ の上のどのような曲線も $\mathcal{M}/{\sim}$ では一点につぶれてしまい動かない為。

残った水平空間 $\mathcal{H}_x$ の方は $T\_{[x]}(\mathcal{M}/{\sim})$ と同型(どちらも $n$ 次元のベクトル空間) になり、任意の $v\in T\_{[x]}(\mathcal{M}/{\sim})$ に対して

$$\mathcal{D}_{\pi}(x)[u] = v$$

となる $u\in \mathcal{H}_x$ が一意に存在する。これを $v$ の $x$ での **水平リフト(horizontal lift)** という。また

$$T_{[x]}(\mathcal{M}/{\sim})\simeq\mathcal{H}_x$$

なのであるから、水平空間の事を接ベクトル空間だと思ってしまっても良い。

{{% example title="実射影空間" %}}
実射影空間 $\mathbb{RP}^{n-1}$ の接ベクトル空間は
$$ T\_{[x]}\mathbb{RP}^{n-1} = \\{z\in\mathbb{R}^n\mid x^Tz=0\\}$$
任意の $\alpha\in\mathbb{R}\_\ast$ と点 $x$ でのリフト $u_x$ に対して
$$ u_{\alpha x}=\alpha u_x $$
が成立する。
{{% /example %}}

実射影空間 $\mathbb{RP}^{n-1}$ は $\mathbb{R}^n\_\ast$ に同値関係

$$x\sim y \Leftrightarrow \exists \alpha\in\mathbb{R}\_\ast,y=\alpha x$$
を入れたものであるので、

$$\pi^{-1}([x]) = \\{\alpha x\mid\alpha\in\mathbb{R}_\ast\\}=x\mathbb{R}\_\ast$$

となる。よって点 $x\in \mathbb{R}^n_\ast$ での垂直空間は

$$\mathcal{V}_x=\\{\alpha x\mid\alpha\in\mathbb{R}\\}=x\mathbb{R}$$

であるから、水平空間として"例えば"

$$\mathcal{H}_x=\\{z\in\mathbb{R}^n\mid x^Tz=0\\}$$

を取ることが出来る。ここで $v\in T_{[x]}\mathbb{RP}^{n-1}$ の点 $x$ でのリフトを $u_x$ とすると、任意の $\alpha\in\mathbb{R}$ に対して $x\sim\alpha x$ であるので

$$\mathrm{D}{\pi}(x)[u_x] = v$$

ここで $\alpha(x) = \alpha x$ とおくと、合成微分則より
$$
\mathrm{D}{\pi}(\alpha(x))[\mathrm{D}{\alpha}(x)[u_x]] = \mathrm{D}{\pi}(x)[u_x]
$$
であり $D_\alpha(x)[u_x] = \alpha u_x$ であるから
$$\mathrm{D}{\pi}(\alpha x)[\alpha u_x] = v$$

これは $v$ の点 $\alpha x$ でのリフト $u_{\alpha x}$ であるので
$$ u_{\alpha x} = \alpha u_x $$
が成り立つ。

グラスマン多様体は実射影空間を一般化したものであったから、この接ベクトル空間も同じような形になる。

{{% example title="グラスマン多様体" %}}
グラスマン多様体 $\mathrm{Grass}(p,n)$ の接ベクトル空間は

$$ T_{[X]}\mathrm{Grass}(p,n) = \\{Z\in\mathbb{R}^{n\times p}\mid X^TZ=0\\} $$

任意の $A\in \mathrm{GL}_p$ と点 $X$ でのリフト $U_x$ に対して

$$ U_{XA}=U_XA$$

である。
{{% /example %}}

接ベクトル空間を集めた集合は、それ自体も多様体と見なすことが出来る。


{{% definition title="接バンドル" %}}
接空間の全ての点での直和
$$ T\mathcal{M} = \bigsqcup\_{x\in\mathcal{M}} T_x\mathcal{M} = \\{(x,v)\mid x\in\mathcal{M},v\in T_x\mathcal{M}\\}$$
を $\mathcal{M}$ の **接バンドル(tangent bundle)** という。
$\dim\mathcal{M}=n$の時、接バンドル $T\mathcal{M}$ は $2n$ 次元多様体見なすことが出来る。
{{% /definition %}}

というのは $\mathcal{M}$ の$x$の周りのチャート $(U,\varphi)$ に対して

$$ \varphi': T_x\mathcal{M}\rightarrow\mathbb{R}^{2n}: v\mapsto (\varphi_1(x),\ldots,\varphi_n(x),v(\varphi_1)(x),\ldots,v(\varphi_n)(x))^T$$

が $T\mathcal{M}$ のチャートとなり、これらを全て集めて $T\mathcal{M}$ のアトラスを構成する事が出来る。

{{% definition title="ベクトル場" %}}
$\mathcal{M}$ の各点 $x$ に接ベクトル空間 $T_x\mathcal{M}$ のベクトルを対応づける滑らかな写像

$$ V:\mathcal{M}\rightarrow T\mathcal{M}: x\rightarrow v\in T_x\mathcal{M} $$

を **ベクトル場(vector field)** という。
{{% /definition %}}

多様体の各点に接ベクトルが1つずつ定められていて、それらが点の移動に関して滑らかに変化していくようなものを表している。

$V(x)$ の事を $V_x$ と書く事にする。そして ベクトル場 $V$, $f\in C(\mathcal{M})$ に対して

$$ Vf(x) := V_x(f) $$

と定める。これは $f$ の点 $x$ における接ベクトル $V_x$ に沿った方向微分。

ベクトル場 $V,V'$ に対して、その加法や $f\in C(\mathcal{M})$ 倍を各点で自然に定める事が出来る。
これらの演算でベクトル場の滑らかさは損なわれない。
$$
\begin{aligned}
(V+V')_x &:= V_x + V'_x \\\\
(fV)_x &:= f(x)V_x
\end{aligned}
$$

あるチャート $(U,\varphi)$ の中では各点 $x$ に接ベクトル空間の$i$番目の標準基底を対応させるベクトル場

$$x\mapsto \left(\frac{\partial}{\partial x_i}\right)_x$$

を考える事が出来る。これを $i$-th coordinate vector field(日本語では？) と呼び $E_i$ と書く。つまり

$$ (E_if)(x) = \left(\frac{\partial f}{\partial x_i}\right)_x = \left(\frac{\partial (f\circ\varphi^{-1})}{\partial x_i}\right)_x$$

のこと。すると、任意のベクトル場は $U$ の中では以下のように分解することが出来る

$$ V = \sum_{i}(V\varphi_i)E_i$$

実際に点 $x$ での $f$ の方向微分を計算してみると $\gamma$ を接ベクトル $V_x$ に対応する適当な曲線として

$$
\begin{aligned}
Vf(x) &= \sum_i((V\varphi_i)E_i)f(x) \\\\
&= \sum_i ((V\varphi_i)E_i)_x(f) \\\\
&= \sum_i (V\varphi_i(x))\ (E_i)_x(f) \\\\
&= \sum_i V_x(\varphi_i)\ (E_if)(x) \\\\
&= \sum_i \frac{\mathrm{d}(\varphi_i\circ\gamma)}{\mathrm{d} t}(0)\left(\frac{\partial (f\circ\varphi^{-1})}{\partial x_i}\right)_x \\\\
&= \frac{\mathrm{d}(f\circ\gamma)}{\mathrm{d}t}(0) \\\\
&= V_x(f)
\end{aligned}$$

となる。
