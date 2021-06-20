---
title: 3. 多様体の位相
---

すでに述べたように、このノートでは多様体の位相は天下り的に与えられるのではなくて、極大アトラスによって定められる。その構成方法について見ていく。

<div class="box" markdown=1>
<div class="title"> 定義:開集合 </div>
$\mathcal{M}$ を集合、 $\mathcal{A}$ を極大アトラスとする。
部分集合 $\mathcal{N}\subset \mathcal{M}$ が$\mathcal{M}$の**開集合(open subset)**であるとは、任意のチャート $(U,\varphi)\in \mathcal{A}$ について $\varphi(\mathcal{N}\cap U)$ が開集合である事をいう。
</div>

<div class="box" markdown=1>
<div class="title"> 命題3.1 </div>
集合 $\mathcal{M}$, 極大アトラス $\mathcal{A}$ の定める開集合の族は開集合の公理を満たす。

1. $\mathcal{M},\emptyset$ は開集合
2. $U,V$ が開集合ならば $U\cap V$ も開集合
3. $\\{U_\alpha\\}$が開集合ならば$\bigcup_\alpha U_\alpha$ も開集合
</div>

Proof.

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
