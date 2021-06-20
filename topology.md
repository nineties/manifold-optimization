---
title: 3. 多様体の位相
---

すでに述べたように、このノートでは多様体の位相は天下り的に与えられるのではなくて、極大アトラスによって定められる。その構成方法について見ていく。

<div class="box" markdown=1>
<div class="title"> 定義:開集合 </div>
$M$ を集合、 $A$ を極大アトラスとする。
部分集合 $N\subset M$ が$M$の**開集合(open subset)**であるとは、任意のチャート $(U,\varphi)\in A$ について $\varphi(N\cap U)$ が開集合である事をいう。
</div>

<div class="box" markdown=1>
<div class="title"> 命題3.1 </div>
集合 $M$, 極大アトラス $A$ の定める開集合の族は開集合の公理を満たす。

1. $M,\emptyset$ は開集合
2. $U,V$ が開集合ならば $U\cap V$ も開集合
3. $\\{U_\alpha\\}$が開集合ならば$\bigcup_\alpha U_\alpha$ も開集合
</div>

Proof.

$M,\emptyset$ が$M$の開集合となる事は明らか。

$U,V$ が開集合であるならば、任意のチャート $(W,\varphi)$ に対して

\\[
\varphi((U\cap V)\cap W) = \varphi((U\cap W)\cap (V\cap W)) = \varphi(U\cap W)\cap\varphi(V\cap W)\quad\text{($\because \varphi$は全単射)}
\\]

であるので $\varphi(U\cap W),\varphi(V\cap W)$ が $\mathbb{R}^d$ の開集合である事より $\varphi((U\cap V)\cap W)$ も$\mathbb{R}^d$の開集合。従って $U\cap V$ の $M$の開集合。

$\\{U_\alpha\\}$ が開集合であるならば、任意のチャート $(V,\varphi)$ に対して
\\[
\varphi\left(\left(\bigcup_\alpha U_\alpha\right)\cap V\right) = \varphi\left(\bigcup_\alpha\left(U_\alpha\cap V\right)\right) = \bigcup_\alpha\varphi(U_\alpha\cap V)
\\]
となることから、同様にして $\bigcup_\alpha U_\alpha$ も $M$ の開集合である。$\square$

<div class="box" markdown=1>
<div class="title"> 定義:アトラス位相 </div>
$M$ とする。 $M$の極大アトラス $A$ の定める開集合の族を開集合系とする位相を **アトラス位相(atlas topology)** という。
</div>
