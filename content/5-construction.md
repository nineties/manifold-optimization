---
title: 5. 多様体の構成方法
section: 5
---

多様体から新しい多様体を作る方法として、直和、積多様体、商多様体について説明する。

{{% definition title="多様体の直和" %}}
次元の等しい多様体 $(\mathcal{M},\mathcal{A}^+),(\mathcal{N},\mathcal{B}^+)$ に対して

$$ (\mathcal{M}\sqcup\mathcal{N},(\mathcal{A}\sqcup\mathcal{B})^+)$$

も同じ次元の多様体となる。これを $\mathcal{M},\mathcal{N}$ の **直和(direct sum)** という。

{{% /definition %}}

直和は、2つの多様体を持ってきてそれらで1つの多様体であるというだけの話なので構成としては特に面白くないが、商多様体を構成する前段で構成したりする。

{{% definition title="積多様体" %}}
$m$ 次元多様体 $(\mathcal{M},\mathcal{A}^+)$、 $n$ 次元多様体 $(\mathcal{N},\mathcal{B}^+)$ に対して
$$\mathcal{A}\times\mathcal{B}=\\{(U\times V,\varphi\times\psi)\mid(U,\varphi)\in\mathcal{A}, (V,\psi)\in\mathcal{B}\\}$$
$$\varphi\times\psi:U\times V\rightarrow\mathbb{R}^m\times\mathbb{R}^n:(x,y)\mapsto(\varphi(x),\psi(y)) $$
とした時、
$$(\mathcal{M}\times\mathcal{N},(\mathcal{A}\times\mathcal{B})^+)$$
は $m+n$ 次元多様体となる。これを **積多様体(product manifold)** という。
{{% /definition %}}

例えば、ユークリッド空間$\mathbb{R}^m$ は$\mathbb{R}$ 複数個の積多様体 $\mathbb{R}^m\simeq\mathbb{R}\times\mathbb{R}\times\cdots\mathbb{R}$ である。一次元球面 $S^1$ と $\mathbb{R}$ の積 $S^1\times\mathbb{R}$ は円柱、 $S^1\times S^1$ は2トーラスといった感じで様々な多様体が積多様体として構成される。

{{% definition title="商多様体" %}}
${\sim}$ を $\mathcal{M}$ 上の同値関係とする。
多様体 $(\mathcal{M},\mathcal{A}^+)$ から多様体 $(\mathcal{M}/{\sim},\mathcal{B}^+)$ への自然な全射が沈め込みとなるとき、$(\mathcal{M}/{\sim},\mathcal{B}^+)$ を$\mathcal{M}$ の ${\sim}$ による **商多様体(quotient manifold)** という。
{{% /definition %}}

部分多様体の時と同様に以下が成立する。

{{% proposition %}}
多様体 $\mathcal{M}$ の同値関係 ${\sim}$ での商集合 $\mathcal{M}/{\sim}$ が商多様体となるような $\mathcal{M}/{\sim}$ の微分構造は一意に定まる。
{{% /proposition %}}

{{< ref ex.y-shape-space >}} のような例もあり、商集合が常に多様体になるわけではない。

{{% proposition %}}
多様体 $\mathcal{M}$ 上の同値関係 ${\sim}$ について、$\mathcal{M}/{\sim}$ が商多様体となる必要十分条件は以下が成り立つ事である。

1. $\mathrm{graph}({\sim}) = \\{(x,y)\in\mathcal{M}\times\mathcal{M}\mid x{\sim} y\\}$ が $\mathcal{M}\times\mathcal{M}$ の部分多様体であり、$\pi:\mathrm{graph}({\sim})\rightarrow\mathcal{M}:(x,y)\mapsto x$ が沈め込みである。

2. $\mathrm{graph}({\sim})$ が $\mathcal{M}\times\mathcal{M}$ の閉集合である。

また、

$$\mathrm{dim}(\mathcal{M}/{\sim})=2\dim(\mathcal{M})-\mathrm{dim}(\mathrm{graph}({\sim}))$$

である。

{{% /proposition %}}

状況をイメージするのが難しいので具体例で考える。$\mathcal{M}=\mathbb{R}$ とし、同値関係を

$$x{\sim} y\Leftrightarrow x-y\in\mathbb{Z}$$

とする。この時 $\mathcal{M}/{\sim}$ は単位円 $S^1$ と微分同相な空間になる。
(この同値関係では、数直線上の小数部分が等しい各点が同じ点になるので、下図のように $S^1$ が出来上がる)

{{< figure src="../images/quotient-space0.png" >}}

これが商多様体となる条件が何を言っているか確認すると、まず $\mathrm{graph}({\sim})$ は以下の図のように直線 $x-y=k,k\in\mathbb{Z}$ を集めた空間になる。

{{< figure src="../images/quotient-space1.png" >}}

ここで $\pi(x,y)=x$ となるような $y$ は $x{\sim} y$ であるものなので $\pi$ は${\sim}$ で同値な点を一点に潰す写像で、これが沈め込みであるという事が商多様体を作る自然な全射が沈め込みであるという事と同値になる。

そして $\mathrm{graph}({\sim})$ が閉集合であるということは、 $\mathcal{M}/{\sim}$ がハウスドルフ空間であるということに対応する。
$\mathrm{graph}({\sim})$ が閉集合であるならば、その補集合 $\mathrm{graph}({\sim})^\circ$ が開集合であるので、任意の点 $(x,y)\in\mathrm{graph}({\sim})^\circ $に対して
$(x,y)\in U\times V$ となる開集合 $U\times V\subset\mathrm{graph}({\sim})^\circ$ が存在する。

ところで $(x,y)\in\mathrm{graph}({\sim})^\circ$ であるということは $x\not{\sim} y$ である事を表すので、このことは $x\not{\sim} y$ であるならば $x\in U,y\in V,U\cap V=\emptyset$ となる開集合 $U,V$ が存在する事と同値。

---

条件を満たさない例として {{< ref ex.y-shape-space >}} ではどうなるかを見てみる。

まず $\mathcal{M}=\mathbb{R}\sqcup\mathbb{R}$ とおき、この上での同値関係を

$$(x,0){\sim}(x',1)\Leftrightarrow x=x', x<0 $$

で定める。このとき

$$
\mathrm{graph}({\sim}) = 
\\{ ((x,0),(x,1)) \mid x < 0 \\} \cup
\\{ ((x,1),(x,0)) \mid x < 0 \\}
$$

となる。すると $\pi$ は沈め込みにはなるので第一の条件は満たすが、閉集合ではない。

{{% proposition %}}
$\mathcal{M}/{\sim}$ が $\mathcal{M}$ の商多様体であるとし、 $\pi:\mathcal{M}\rightarrow\mathcal{M}/{\sim}$ を自然な全射とする。

$\mathrm{dim}(\mathcal{M}/{\sim}) < \mathrm{dim}(\mathcal{M})$ であるならば、任意の同値類 $[x]\in\mathcal{M}/{\sim}$ について $\pi^{-1}([x])$ は $\mathcal{M}$ の
$\mathrm{dim}(\mathcal{M}) - \mathrm{dim}(\mathcal{M}/{\sim})$ 次元部分多様体である。
{{% /proposition %}}

{{< ref th.submersion-theorem >}} より。

商多様体上の可微分写像に関して、以下が言える。

{{% proposition %}}

可微分写像 $f:\mathcal{M}\rightarrow\mathcal{N}$ が同値関係 $\sim$ に関して不変 ($x\sim y\Rightarrow f(x)=f(y)$) であるならば、

$$\tilde{f}\circ\pi=f$$

となるような連続写像 $\tilde{f}:\mathcal{M}/{\sim}\rightarrow\mathcal{N}$ が一意に存在する。
{{% /proposition %}}

$f$ が不変であるということは、$\tilde{f}([x])=f(x)$ の値が $x$ の選び方に寄らない($\tilde{f}$がwell-definedである)ということ。

{{% example title="実射影空間" label="ex.real-projective-space" %}}
$\mathbb{R}^n\_\ast = \mathbb{R}^n\setminus\\{0\\}$ を同値関係
$$ x\sim y \Leftrightarrow \exists t\in\mathbb{R}\_\ast, y=tx $$
で割った空間は $n-1$次多様体となる。これを **実射影空間(real projective space)** といい
$$\mathbb{RP}^{n-1}\simeq\mathbb{R}^n\_\ast/{\sim}$$
と書く。
{{% /example %}}

方向が一致するベクトルを同一視した空間であるので「$\mathbb{R}^n$ の方向の集合」といえる。もしくは「$\mathbb{R}^n$ の1次元部分空間の集合」と考えることもできる。後者の考え方を一般化すると、次の概念を得る。

{{% example title="グラスマン多様体" label="ex.grassmann-manifold" %}}

ノンシュティーフェル多様体 $\mathbb{R}^{n\times p}\_\ast$ 上の同値関係を
$$X\sim Y\Leftrightarrow \mathrm{span}(X)=\mathrm{span}(Y)$$
とすると
$$\mathrm{Grass}(p,n)=\mathbb{R}^{n\times p}\_\ast/{\sim}$$
は $p(n-p)$ 次元多様体となる。これを **グラスマン多様体(Grassmann manifold)** という。
{{% /example %}}

つまり、$\mathrm{Grass}(p,n)$ とは$\mathbb{R}^n$ の $p$ 次元部分空間の集合。
例えば $\mathrm{Grass}(2,3)$ は $\mathbb{R}^3$ の中の原点を通る平面の集合。各平面が1つの点となる多様体なのでなかなか想像は難しい。

$\mathrm{span}(X)=\mathrm{span}(Y)$ であるというのは適当な基底変換 $P\in \mathrm{GL}_p$ が存在して $Y=XP$ と書けるという事であるから、 $X$ の同値類は

$$[X] = \\{XP\mid P\in \mathrm{GL}_p\\}$$

とも書ける。この意味で $\mathrm{Grass}(p,n)$ を $\mathbb{R}^{n\times p}\_\ast/\mathrm{GL}_p$ とも書く。
