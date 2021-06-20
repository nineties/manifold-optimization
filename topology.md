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
$\mathcal{M}$ とする。 $\mathcal{M}$の極大アトラス $\mathcal{A}$ の定める開集合の族を開集合系とする位相を **アトラス位相(atlas topology)** という。
</div>

$U\subset\mathcal{M}$ が開集合であるか否かの判定に極大アトラス $\mathcal{A}$ の全てのチャートを調べるのは大変なので、以下の命題を示す。

<div class="box" markdown=1>
<div class="title"> 命題 3.1 </div>
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

ここで仮定より $\varphi_\beta(U\cap U_\beta)$ は開集合、 $\mathcal{B}\subset\mathcal{A}$ より $\varphi_\beta(U_\alpha\cap U_\beta$ も開集合。よってこれらの共通部分も開集合であり、その微分同相写像 $\varphi_\alpha\circ\varphi_\beta^{-1}$ での逆像も開集合。そしてそれらの和集合は開集合。以上より $\varphi_\alpha(U\cap U_\alpha)$ も開集合となる。 $\square$

<div class="box" markdown=1>
<div class="title"> 命題 3.2 </div>
多様体の任意の開集合は多様体である
</div>

証明

$(\mathcal{M},\mathcal{A})$ を多様体とし、 $U\subset\mathcal{M}$ をその開集合とする。ここで $\mathcal{A}$ の全てのチャートを $U$ に制限した

\\[
\mathcal{A}\_U=\\{(U\cap U_\alpha,\varphi_\alpha\|_{U\cap U\_\alpha})\ \|\ (U\_\alpha,\varphi\_\alpha)\in\mathcal{A}\\}
\\]

を考える。これが $U$ の極大アトラスとなり、可算被覆を持つこととハウスドルフ性を満たす事を示せば良い。


$U$ は開集合だから
$\varphi(U\cap U_\alpha)$ は $\mathbb{R}^d$ の開集合。そして $\varphi_\alpha\|\_{U\cap U\_\alpha}$ は全単射だから $(U\cap U\_\alpha,\varphi\_\alpha\|\_{U\cap U\_\alpha})$ はチャート。さらに $\bigcup_\alpha (U\cap U_\alpha) = U\cap\left(\bigcup_\alpha U_\alpha\right) = U\cap\mathcal{M} = U$ だから $\mathcal{A}_U$ はアトラス。

$\mathcal{A}_U$ が極大アトラスではないとすると、 $\mathcal{A}_U$ に含まれないチャート $(V,\psi)$ で $\mathcal{A}_U$ と両立するものが存在。$\mathcal{N}$ のチャートは $\mathcal{M}$ のチャートでもあるから $\mathcal{A}$ が極大アトラスである事より $(V,\psi)\in\mathcal{A}$。この時 $U\cap V=V$ だから $(V,\psi)\in\mathcal{A}_U$ となり矛盾。よって $\mathcal{A}_U$ は $U$ の極大アトラス。

$\mathcal{A}$は可算被覆を持つから、それらと $U$ の共通部分を取る事で $\mathcal{A}_U$ の可算被覆を作れる。

$x,y\in U,x\neq y$ とする。 $\mathcal{M}$ のハウスドルフ性より $\mathcal{M}$ のチャート $U_\alpha,U_\beta$ で

\\[ x\in U_\alpha, y\in U_\beta, U_\alpha\cap U_\beta = \emptyset \\]

となるものが取れる。これらを $U$ に制限すれば $x,y$ を分離する $U$ のチャートが得られる。 $\square$

---

<div class="box" markdown=1>
<div class="title"> 命題 3.3 </div>
$\mathcal{M}$ を集合、 $\mathcal{A}$ を極大アトラスとする。この時 $\mathcal{A}$ は $\mathcal{M}$ の開集合系の**基底 (base)** である。

すなわち、任意の開集合 $U$ は $\mathcal{A}$ のチャート $U_\alpha$ の和集合として表すことができる。
</div>

証明

$U$は開集合だから チャート $(U_\alpha,\varphi_\alpha)$ と $U$ の共通部分を取った $(U\cap U\_\alpha, \varphi_\alpha\|\_{U\cap U_\alpha})$ も $\mathcal{M}$ のチャートである。これが $\mathcal{A}$ の全てのチャートと両立する事は簡単に示せて $(U\cap U\_\alpha, \varphi_\alpha\|\_{U\cap U_\alpha})\in\mathcal{A}$ である。よって $U = \bigcup_\alpha(U\cap U_\alpha)$である事より示された。 $\square$
