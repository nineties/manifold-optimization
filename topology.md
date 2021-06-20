---
title: 3. 多様体の位相
---

すでに述べたように、このノートでは多様体の位相は天下り的に与えられるのではなくて、極大アトラスによって定められる。その構成方法について見ていく。

<div class="box" markdown=1>
<div class="title"> 定義:開集合 </div>
$\mathcal{M}$ を集合、 $\mathcal{A}$ を極大アトラスとする。
部分集合 $\mathcal{N}\subset \mathcal{M}$ が$\mathcal{M}$の**開集合(open subset)**であるとは、任意のチャート $(U,\varphi)\in \mathcal{A}$ について $\varphi(\mathcal{N}\cap U)$ が開集合である事をいう。
</div>

$U$ が開集合であるというのは、どの地図上でその部分を見ても開集合になっているという事。

<div class="box" markdown=1>
<div class="title"> 命題3.1 </div>
集合 $\mathcal{M}$, 極大アトラス $\mathcal{A}$ の定める開集合の族は開集合の公理を満たす。

1. $\mathcal{M},\emptyset$ は開集合
2. $U,V$ が開集合ならば $U\cap V$ も開集合
3. $\\{U_\alpha\\}$が開集合ならば$\bigcup_\alpha U_\alpha$ も開集合
</div>

証明

$\mathcal{M},\emptyset$ が$\mathcal{M}$の開集合となる事は明らか。

$U,V$ が開集合であるならば、任意のチャート $(W,\varphi)$ に対して

\\[
\varphi((U\cap V)\cap W) = \varphi((U\cap W)\cap (V\cap W)) = \varphi(U\cap W)\cap\varphi(V\cap W)\quad\text{($\because \varphi$は全単射)}
\\]

であるので $\varphi(U\cap W),\varphi(V\cap W)$ が $\mathbb{R}^d$ の開集合である事より $\varphi((U\cap V)\cap W)$ も$\mathbb{R}^d$の開集合。従って $U\cap V$ の $\mathcal{M}$の開集合。

$\\{U_\alpha\\}$ が開集合であるならば、任意のチャート $(V,\varphi)$ に対して
\\[
\varphi\left(\left(\bigcup_\alpha U_\alpha\right)\cap V\right) = \varphi\left(\bigcup_\alpha\left(U_\alpha\cap V\right)\right) = \bigcup_\alpha\varphi(U_\alpha\cap V)
\\]
となることから、同様にして $\bigcup_\alpha U_\alpha$ も $\mathcal{M}$ の開集合である。$\square$

<div class="box" markdown=1>
<div class="title"> 定義:アトラス位相 </div>
$\mathcal{M}$ を集合とする。 $\mathcal{M}$の極大アトラス $\mathcal{A}$ の定める開集合の族を開集合系とする位相を **アトラス位相(atlas topology)** という。
</div>

以後、特に断りがなければ、$(\mathcal{M},\mathcal{A})$ の位相はアトラス位相によって与えられるとする。
アトラス位相を導入すると、チャートはよくある多様体の定義で仮定される性質を満たすようになる。

<div class="box" markdown=1>
<div class="title"> 命題3.2 </div>
$\mathcal{M}$ を集合 $\mathcal{A}$ を極大アトラスとする。
任意のチャート $(U,\varphi)\in\mathcal{A}$ について $U$ は開集合であり、 $\varphi:U\rightarrow\varphi(U)$ は同相写像である。
</div>

まず、次の一般的な事実を確認する。

チャート $(U,\varphi)$ と $U$の部分集合 $V\subset U$ について $\varphi(V)$ が $\mathbb{R}^d$ の開集合ならば、 $(V,\varphi\|_V)$ もチャートである。そして $(U,\varphi)$ と $(V,\varphi\|_V)$ は両立する。また、$(U,\varphi)$ がアトラス $\mathcal{A}$ と両立するならば $(V,\varphi\|_V)$ も $\mathcal{A}$ と両立する。この事は $\varphi\circ\varphi\|_V^{-1}$ が恒等写像となる事から簡単に示せる。

証明

$(U,\varphi)$ と $\mathcal{A}$ が両立する事から $U$ が開集合であるのは明らか。

任意の開集合 $V\subset\varphi(U)$ の $\varphi$ の逆像 $\varphi^{-1}(V)$ は $U$ の部分集合だから $\left(\varphi^{-1}(V),\varphi\|_{\varphi^{-1}(V))}\right)$ も $\mathcal{A}$ と両立するチャートである。従って $\varphi^{-1}(V)$ は開集合だから $\varphi:U\rightarrow\varphi(U)$ は連続。

また、任意の開集合 $W\subset U$ に対して $\varphi(W)=\varphi(W\cap U)$ は開集合だから $\varphi^{-1}:\varphi(U)\rightarrow U$ も連続。$\square$

<div class="box" markdown=1>
<div class="title"> 命題3.3 </div>

</div>

<div class="box" markdown=1>
<div class="title"> 命題3.3 </div>
$\mathcal{M}$ を集合、 $\mathcal{A}$ を極大アトラスとする。この時 $\mathcal{A}$ は $\mathcal{M}$ の開集合系の**基底 (base)** である。
すなわち、任意の開集合 $U$ は $\mathcal{A}$ のチャート $U_\alpha$ の和集合として表すことができる。
</div>

証明

$U$は開集合だから任意のチャート $(U_\beta,\varphi_\beta)\in\mathcal{A}$ について $U\cap U_\beta$ は開集合。


$\varphi_\alpha(U\cap U_\alpha)$ は開集合である。そして、$U\cap U_\alpha\subset U_\alpha$であるから$(U\cap U\_\alpha, \varphi_\alpha\|\_{U\cap U_\alpha})$ もチャートである。そして $(U_\alpha,\varphi_\alpha)\in\mathcal{A})$ である事より $(U\cap U\_\alpha, \varphi_\alpha\|\_{U\cap U_\alpha})$ は $\mathcal{A}$ と両立するが、$\mathcal{A}$ は極大アトラスなので
$(U\cap U\_\alpha, \varphi_\alpha\|\_{U\cap U_\alpha})\in\mathcal{A}$
よって $U = \bigcup_\alpha(U\cap U_\alpha)$である事より示された。 $\square$


$U\subset\mathcal{M}$ が開集合であるか否かを判定するのに極大アトラス $\mathcal{A}$ の全てのチャートを調べる必要はない。

<div class="box" markdown=1>
<div class="title"> 命題 3.4 </div>
$\mathcal{M}$ を集合、 $\mathcal{A}$ を極大アトラスとする。
部分集合 $U\subset\mathcal{M}$ が開集合である事は、適当な $U$ を覆うアトラス $\mathcal{B}\subset\mathcal{A}$ の任意のチャート $(U_\beta,\varphi_\beta)\in\mathcal{B}$ について $\varphi_\beta(U\cap U_\beta)$ が開集合である事と同値。
</div>

証明

$U$ がアトラス $\mathcal{B}$ について条件を満たすとする。この時、任意のチャート $(U_\alpha,\varphi_\alpha)\in\mathcal{A}$ について

\\[
\begin{aligned}
\varphi_\alpha(U\cap U_\alpha) &= \bigcup_{\beta}\varphi_\alpha(U\cap U_\alpha\cap U_\beta) \\\\ \\\\
&= \bigcup_\beta(\varphi_\alpha\circ\varphi_\beta^{-1})(\varphi_\beta(U\cap U_\alpha\cap U_\beta)) \\\\ \\\\
&= \bigcup_\beta(\varphi_\alpha\circ\varphi_\beta^{-1})(\varphi_\beta((U\cap U_\beta)\cap(U_\alpha\cap U_\beta))) \\\\ \\\\
&= \bigcup_\beta(\varphi_\alpha\circ\varphi_\beta^{-1})\left(\varphi_\beta(U\cap U_\beta)\cap\varphi_\beta(U_\alpha\cap U_\beta)\right) \\\\ \\\\
\end{aligned}
\\]

である。ただし、$\beta$ に関しての和は $\mathcal{B}$ の全てのチャートに対して取る。

ここで仮定より $\varphi_\beta(U\cap U_\beta)$ は開集合、 $\mathcal{B}\subset\mathcal{A}$ より $\varphi_\beta(U_\alpha\cap U_\beta)$ も開集合。よってこれらの共通部分も開集合であり、その微分同相写像 $\varphi_\alpha\circ\varphi_\beta^{-1}$ での逆像も開集合。そしてそれらの和集合は開集合。以上より $\varphi_\alpha(U\cap U_\alpha)$ も開集合となる。 $\square$

<div class="box" markdown=1>
<div class="title"> 命題 3.5 </div>
多様体の任意の開集合は多様体である
</div>

証明

$(\mathcal{M},\mathcal{A})$ を多様体とし、 $U\subset\mathcal{M}$ をその開集合とする。
ここで $U$ に含まれるチャートだけを集めた

\\[ \mathcal{A}_U =\\{(V,\psi)\ \|\ (V,\psi)\in\mathcal{A},V\subset U\\}\\]

を考える。これが $U$ の極大アトラスとなるのは明らか。

$\mathcal{A}$は可算被覆を持つから、それらと $U$ の共通部分を取る事で $\mathcal{A}_U$ の可算被覆を作れる。($U$ は開集合だから任意の $U\_\alpha$ に対して $U\cap U\_\alpha$ はチャートである事に注意)

$x,y\in U,x\neq y$ とする。 $\mathcal{M}$ のハウスドルフ性より $\mathcal{M}$ のチャート $U_\alpha,U_\beta$ で

\\[ x\in U_\alpha, y\in U_\beta, U_\alpha\cap U_\beta = \emptyset \\]

となるものが取れる。これらを $U$ に制限すれば $x,y$ を分離する $U$ のチャートが得られる。 $\square$

<div class="box" markdown=1>
<div class="title"> 命題 3.6 </div>
$\mathcal{M}$を集合, $\mathcal{A}$ を極大アトラスとすると

$(\mathcal{M},\mathcal{A})$ がハウスドルフ性を持つ $\Leftrightarrow$ $\mathcal{A}$ の定めるアトラス位相で$\mathcal{M}$がハウスドルフ空間となる
</div>

証明

($\Rightarrow$)
$\mathcal{A}$ がアトラス位相の基底である事から明らか。

($\Leftarrow$)
$x,y\in\mathcal{M},x\neq y$ とする。 $\mathcal{M}$ はハウスドルフ空間だから開集合 $U,V\subset\mathcal{M}$ が存在して

\\[ x\in U,y\in V,U\cap V=\emptyset \\]

となる。$U,V$ は開集合だから、それぞれ $\mathcal{A}$ のチャートの和集合で表す事ができ、その中に $x,y$ を含む互いに交わらないチャートが存在する。$\square$


<div class="box" markdown=1>
<div class="title"> 命題 3.7 </div>
$\mathcal{M}$を集合, $\mathcal{A}$ を極大アトラスとすると

$(\mathcal{M},\mathcal{A})$ が可算被覆を持つ $\Leftrightarrow$ $\mathcal{A}$ の定めるアトラス位相で$\mathcal{M}$が第二可算空間となる
</div>

(この命題が成り立つのか、以下の証明が正しいのか、ちょっと自信がない。)

まず、ユークリッド空間 $\mathbb{R}^d$ は第二可算空間である事を確認する。つまり可算個の基底が存在して、それらの和集合で全ての開集合が表せる。基底としては中心が有理点、半径が正の有理数であるような全ての開球をとれば良い。

証明

($\Leftarrow$)は明らかなので($\Rightarrow$)を示せば良い。

$\mathcal{B}=\\{B_1,B_2,\ldots\\}$ をユークリッド空間 $\mathbb{R}^d$ の可算基底とする。
$(\mathcal{M},\mathcal{A})$ は可算被覆を持つので、それを $(U_1,\varphi_1),(U_2,\varphi_2),\ldots\in\mathcal{A}$ とすると $\mathcal{M}=\bigcup_i U_i$ である。

ここで $\varphi_i$ は同相写像だから $V_{ij}=\varphi_i^{-1}(B_j)$ は $\mathcal{M}$ の開集合。これらを全て集めた集合 $\mathcal{V}=\\{V_{ij}\\}$ は可算集合である。

任意の $\mathcal{M}$ の開集合 $U\subset\mathcal{M}$ と $i$ について $\varphi_i(U\cap U_i)$ は $\mathbb{R}^d$ の開集合だから$\mathcal{B}$に含まれる開集合の和で表される。従って $U\cap U_i$ は$\\{\varphi_i^{-1}(B_1),\varphi_i^{-1}(B_2),\ldots\\}\subset\mathcal{V}$ に含まれる開集合の和で表される。よって $U=\bigcup_i(U\cap U_i)$ だから $U$ は $\mathcal{V}$ に含まれる開集合の和で表される。

以上より $\mathcal{V}$ が $\mathcal{M}$ の可算基底になっている事から $\mathcal{M}$ は第二可算空間となる。 $\square$
