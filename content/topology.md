---
title: 3. 多様体の位相構造
section: 3
---

すでに述べたように、このノートでは多様体の位相は天下り的に与えられるのではなくて、極大アトラスによって定められる。その構成方法について見ていく。

{{% definition title="開集合" %}}
$\mathcal{M}$ を集合、 $\mathcal{A}$ を極大アトラスとする。
部分集合 $\mathcal{N}\subset \mathcal{M}$ が$\mathcal{M}$の **開集合(open subset)** であるとは、任意のチャート $(U,\varphi)\in \mathcal{A}$ について $\varphi(\mathcal{N}\cap U)$ が開集合である事をいう。
{{% /definition %}}

$U$ が開集合であるというのは、どの地図上でその部分を見ても開集合になっているという事。

{{% proposition %}}
集合 $\mathcal{M}$ の極大アトラスの定める開集合の族は開集合の公理を満たす。すなわち、

1. $\mathcal{M},\emptyset$ は開集合
2. $U,V$ が開集合ならば $U\cap V$ も開集合
3. $\\{U_\alpha\\}$が開集合ならば$\bigcup_\alpha U_\alpha$ も開集合
{{% /proposition %}}

証明

$\mathcal{M},\emptyset$ が$\mathcal{M}$の開集合となる事は明らか。

$U,V$ が開集合であるならば、任意のチャート $(W,\varphi)$ に対して

$$\varphi((U\cap V)\cap W) = \varphi((U\cap W)\cap (V\cap W)) = \varphi(U\cap W)\cap\varphi(V\cap W)\quad\text{($\because \varphi$は全単射)}$$

であるので $\varphi(U\cap W),\varphi(V\cap W)$ が $\mathbb{R}^d$ の開集合である事より $\varphi((U\cap V)\cap W)$ も$\mathbb{R}^d$の開集合。従って $U\cap V$ は $\mathcal{M}$の開集合。

$\\{U_\alpha\\}$ が開集合であるならば、任意のチャート $(V,\varphi)$ に対して
$$\varphi\left(\left(\bigcup_\alpha U_\alpha\right)\cap V\right) = \varphi\left(\bigcup_\alpha\left(U_\alpha\cap V\right)\right) = \bigcup_\alpha\varphi(U_\alpha\cap V)$$
となることから、同様にして $\bigcup_\alpha U_\alpha$ も $\mathcal{M}$ の開集合。$\square$

{{% definition title="アトラス位相" %}}
$\mathcal{M}$ を集合とする。 $\mathcal{M}$の極大アトラス $\mathcal{A}$ の定める開集合族の定める位相を **アトラス位相(atlas topology)** という。
{{% /definition %}}

以後、特に断りがなければ、$(\mathcal{M},\mathcal{A})$ の位相はアトラス位相によって与えられるとする。
アトラス位相の下では、よくある多様体の定義と同じくチャートが同相写像となる。

{{% proposition %}}
$\mathcal{M}$ を集合 $\mathcal{A}$ を極大アトラスとする。
任意のチャート $(U,\varphi)\in\mathcal{A}$ について $U$ は開集合であり、 $\varphi:U\rightarrow\varphi(U)$ は同相写像である。
{{% /proposition %}}

証明

$(U,\varphi)$ と $\mathcal{A}$ が両立する事から $U$ が開集合であるのは明らか。

任意の開集合 $V\subset\varphi(U)$ に対して、チャート $\varphi$ を $\varphi^{-1}(V)$ に制限したものも $\mathcal{A}$ と両立するチャートになる。($\because${{< ref prop.subchart-is-chart >}}) よって $\varphi^{-1}(V)$ は開集合だから $\varphi:U\rightarrow\varphi(U)$ は連続

逆に、任意の開集合 $W\subset U$ に対して $\varphi(W)=\varphi(W\cap U)$ は開集合だから $\varphi^{-1}:\varphi(U)\rightarrow U$ も連続。
よって $\varphi$ は同相写像。 $\square$

{{% lemma label="lem.maximal-atlas-is-base" %}}
$\mathcal{M}$ を集合、 $\mathcal{A}$ を極大アトラスとする。この時 $\mathcal{A}$ は $\mathcal{M}$ の開集合系の**基底 (base)** である。
すなわち、任意の開集合 $U$ は $\mathcal{A}$ のチャート $U_\alpha$ の和集合として表すことができる。
{{% /lemma %}}

証明

{{< ref prop.subchart-is-chart >}} より任意のチャート $(U_\alpha,\varphi_\alpha)\in\mathcal{A}$ に対して $U_\alpha$ の開部分集合 (を定義域に持つチャート)は $\mathcal{A}$ のチャートである。

$U$を任意の開集合とすると、$\mathcal{A}$ に属す開集合 $U_\alpha$ について$U\cap U_\alpha(\subset U_\alpha)$ も $\mathcal{A}$ に属すチャートである。よって $U$ は $\mathcal{A}$ に含まれるチャートの和集合 $U = \bigcup_\alpha(U\cap U_\alpha)$ として表される。 $\square$


$U\subset\mathcal{M}$ が開集合であるか否かを判定するのに極大アトラス $\mathcal{A}$ の全てのチャートを調べる必要はない。

{{% proposition %}}
$\mathcal{M}$ を集合、 $\mathcal{A}$ を極大アトラスとする。
部分集合 $U\subset\mathcal{M}$ が開集合である事は、適当な $U$ を覆うアトラス $\mathcal{B}\subset\mathcal{A}$ の任意のチャート $(U_\beta,\varphi_\beta)\in\mathcal{B}$ について $\varphi_\beta(U\cap U_\beta)$ が開集合である事と同値。
{{% /proposition %}}

証明

$U$ がアトラス $\mathcal{B}$ について条件を満たすとする。この時、任意のチャート $(U_\alpha,\varphi_\alpha)\in\mathcal{A}$ について

$$
\begin{aligned}
\varphi_\alpha(U\cap U_\alpha) &= \bigcup_{\beta}\varphi_\alpha(U\cap U_\alpha\cap U_\beta) \\\\
&= \bigcup_\beta(\varphi_\alpha\circ\varphi_\beta^{-1})(\varphi_\beta(U\cap U_\alpha\cap U_\beta)) \\\\
&= \bigcup_\beta(\varphi_\alpha\circ\varphi_\beta^{-1})(\varphi_\beta((U\cap U_\beta)\cap(U_\alpha\cap U_\beta))) \\\\
&= \bigcup_\beta(\varphi_\alpha\circ\varphi_\beta^{-1})\left(\varphi_\beta(U\cap U_\beta)\cap\varphi_\beta(U_\alpha\cap U_\beta)\right) \\\\
\end{aligned}
$$

である。ただし、$\beta$ に関しての和は $\mathcal{B}$ の全てのチャートに対して取る。

ここで仮定より $\varphi_\beta(U\cap U_\beta)$ は開集合、 $\mathcal{B}\subset\mathcal{A}$ より $\varphi_\beta(U_\alpha\cap U_\beta)$ も開集合。よってこれらの共通部分も開集合であり、その微分同相写像 $\varphi_\alpha\circ\varphi_\beta^{-1}$ での逆像も開集合。そしてそれらの和集合は開集合。以上より $\mathcal{A}$ の任意のチャートに対して $\varphi_\alpha(U\cap U_\alpha)$ が開集合となるから $U$ は開集合である。逆は明らか。 $\square$

{{% proposition %}}
多様体の任意の開集合は多様体である
{{% /proposition %}}

証明

$(\mathcal{M},\mathcal{A})$ を多様体とし、 $U\subset\mathcal{M}$ をその開集合とする。
ここで $U$ に含まれるチャートだけを集めた

$$ \mathcal{A}_U =\\{(V,\psi)\ \|\ (V,\psi)\in\mathcal{A},V\subset U\\} $$

を考える。これが $U$ の極大アトラスとなるのは明らか。

$\mathcal{A}$は可算被覆を持つから、それらと $U$ の共通部分を取る事で $\mathcal{A}_U$ の可算被覆を作れる。

$x,y\in U,x\neq y$ とする。 $\mathcal{M}$ のハウスドルフ性より $\mathcal{M}$ のチャート $U_\alpha,U_\beta$ で

$$x\in U_\alpha, y\in U_\beta, U_\alpha\cap U_\beta = \emptyset $$

となるものが取れる。これらを $U$ に制限すれば $x,y$ を分離する $U$ のチャートが得られる。 $\square$

---

最後にアトラス位相が第二可算公理とハウスドルフ性を示す事を証明する。

{{% proposition %}}
$\mathcal{M}$を集合, $\mathcal{A}$ を極大アトラスとすると

$(\mathcal{M},\mathcal{A})$ が可算被覆を持つ $\Leftrightarrow$ $\mathcal{A}$ の定めるアトラス位相で$\mathcal{M}$が第二可算空間となる
{{% /proposition %}}

まず、ユークリッド空間 $\mathbb{R}^d$ は第二可算空間である。つまり可算個の基底が存在して、それらの和集合で全ての開集合が表せる。これは中心が有理点、半径が正の有理数であるような全ての開球の集合が基底となる事から分かる。

証明

($\Leftarrow$)は明らかなので($\Rightarrow$)を示せば良い。

$\mathcal{B}=\\{B_1,B_2,\ldots\\}$ をユークリッド空間 $\mathbb{R}^d$ の可算基底とする。
$(\mathcal{M},\mathcal{A})$ は可算被覆を持つので、それを $(U_1,\varphi_1),(U_2,\varphi_2),\ldots\in\mathcal{A}$ とすると $\mathcal{M}=\bigcup_i U_i$ である。

ここで $\varphi_i$ は同相写像だから $V_{ij}=\varphi_i^{-1}(B_j)$ は $\mathcal{M}$ の開集合。これらを全て集めた集合 $\mathcal{V}=\\{V_{ij}\\}$ は可算集合である。

任意の $\mathcal{M}$ の開集合 $U\subset\mathcal{M}$ と $i$ について $\varphi_i(U\cap U_i)$ は $\mathbb{R}^d$ の開集合だから$\mathcal{B}$に含まれる開集合の和で表される。従って $U\cap U_i$ は$\\{\varphi_i^{-1}(B_1),\varphi_i^{-1}(B_2),\ldots\\}\subset\mathcal{V}$ に含まれる開集合の和で表される。よって $U=\bigcup_i(U\cap U_i)$ だから $U$ は $\mathcal{V}$ に含まれる開集合の和で表される。

以上より $\mathcal{V}$ が $\mathcal{M}$ の可算基底になっている事から $\mathcal{M}$ は第二可算空間となる。 $\square$

{{% proposition %}}
$\mathcal{M}$を集合, $\mathcal{A}$ を極大アトラスとすると

$(\mathcal{M},\mathcal{A})$ がハウスドルフ性を持つ $\Leftrightarrow$ $\mathcal{A}$ の定めるアトラス位相で$\mathcal{M}$がハウスドルフ空間となる
{{% /proposition %}}

証明

($\Rightarrow$)
$\mathcal{A}$ がアトラス位相の基底である事から明らか。

($\Leftarrow$)
$x,y\in\mathcal{M},x\neq y$ とする。 $\mathcal{M}$ はハウスドルフ空間だから開集合 $U,V\subset\mathcal{M}$ が存在して

$$ x\in U,y\in V,U\cap V=\emptyset $$

となる。$U,V$ は開集合だから、それぞれ $\mathcal{A}$ のチャートの和集合で表す事ができ、その中に $x,y$ を含む互いに交わらないチャートが存在する。$\square$
