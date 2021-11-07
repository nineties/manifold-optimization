---
title: 7. 微分
section: 7
---

{{< ref def.differential >}} で定めたバナッハ空間の間の写像 $f:V\rightarrow W$ の微分 $\mathrm{D}f(a)[-]$ を接ベクトル空間に対して一般化する。

{{% definition %}}
多様体の間の滑らかな写像 $F:\mathcal{M}\rightarrow\mathcal{N}$ と、接ベクトル $v\in T_x\mathcal{M}$ に対して、
$$(\mathrm{D}F(x)[v])(f) := v(f\circ F)$$
と定めると $\mathrm{D}F(x)[v]$ は $\mathcal{N}$の$F(x)$ における接ベクトルとなる。この対応

$$ \mathrm{D}F(x):T_x\mathcal{M}\rightarrow T\_{F(x)}\mathcal{N}: v\mapsto\mathrm{D}F(x)[v] $$

は線型写像になり、これを $F$ の $x$ における **微分(differential)** という。
{{% /definition %}}

もし $\mathcal{M},\mathcal{N}$ がベクトル空間の場合は同型 $T\_x\mathcal{M}\simeq\mathcal{M}, T\_{F(x)}\mathcal{N}\simeq\mathcal{N}$ によって $v$ は普通のベクトル $v\in\mathcal{M}$ となり、 $F$ の微分は

$$ \mathrm{D}F(x)[v] = \lim\_{t\rightarrow 0}\frac{F(x+vt)-F(x)}{t} $$

となって、普通の方向微分になる。

