---
title: 6. 接ベクトル空間
section: 6
---

多様体上での最適化を行う上では、点 $x\in\mathcal{M}$ での勾配、もしくは方向微分に相当するものを考える必要がある。({{< ref def.differential >}} の方向微分はバナッハ空間の写像に対するもの)

多様体 $\mathcal{M}$ 上の実数値関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ の点 $x\in\mathcal{M}$ での方向 $\eta$ についての方向微分は
$$ \mathrm{D}\_{f}(x)[\eta] = \lim_{t\rightarrow 0}\frac{f(x+t\eta)-f(x)}{t} $$

みたいな感じで書けそうな気がするが、多様体上の点 $x$ について加算は定義されていない。そもそも $\eta$ をどう表現するかも明らかではない。チャートを使うというのが一つの方法だが、そうするとチャートの選び方に依存したものとなり使い勝手が悪い。

そこで、可微分写像 $\gamma:\mathbb{R}\rightarrow\mathcal{M}$ であって $\gamma(0)=x$ を満たすものを考える。このような写像を $\mathcal{M}$ 上の **曲線(curve)** という。

{{< figure src="../images/curve.png" >}}

これで、 $\mathcal{M}$ 上の点の移動を表すことができるようになったが、その差分 $\gamma(0 + t) - \gamma(0)$ を計算する方法が無い。ただ、上で求めたかった方向微分はこの考え方で求めることができて

$$\lim_{t\rightarrow 0}\frac{f(\gamma(t))-f(\gamma(0))}{t} = 
\left.\frac{\mathrm{d}}{\mathrm{d}t}f\circ\gamma(t)\right|_{t=0}
$$

となる($\because$ $f\circ\gamma:\mathbb{R}\rightarrow\mathbb{R}$は $C^\infty$ 級関数)。 これはチャートの選び方に寄らないが、もちろん $f$ の選び方に依存して決まる量である。

そこで、チャートにも $f$ にも寄らないものとして 

$$f\longmapsto
\left.\frac{\mathrm{d}}{\mathrm{d}t}f\circ\gamma(t)\right|_{t=0}
$$
という **作用素** を考えて、これを接ベクトルと呼ぶ。

{{% definition title="接ベクトル" %}}
$\mathcal{F}_x$ を $x\in\mathcal{M}$ の近傍で定義される$\mathbb{R}$への可微分写像の集合とする。

$x$を通る曲線 $\gamma:\mathbb{R}\rightarrow\mathcal{M}, \gamma(0)=x$ に対して、写像 $\xi_x:\mathcal{F}_x\rightarrow\mathbb{R}$ 

$$ \xi_x(f) = \left.\frac{\mathrm{d}}{\mathrm{d}t}f(\gamma(t))\right|_{t=0}$$


を $x$ における $\mathcal{M}$ の **接ベクトル(tangent vector)** という。

{{% /definition %}}

作用素を接ベクトルというと言われてもイメージが湧かないので具体例を考える。$\mathcal{M}=\mathbb{R}^2$ として、

$$\gamma(t) = (\cos t,\sin t)^T $$

という曲線を考える。単位円を反時計回りに回る曲線である。任意の可微分写像 $f:\mathbb{R}^2\rightarrow\mathbb{R}$ に対して

$$
\frac{\mathrm{d}}{\mathrm{d}t}f(\cos t,\sin t) = -f_x\sin t + f_y\cos t = \begin{pmatrix}f_x & f_y\end{pmatrix}\begin{pmatrix} -\sin t \\\\ \cos t \end{pmatrix}
$$

となるが、ここで馴染みのある $\gamma$ の接ベクトルの表現 $\gamma'(t):=(-\sin t\ \cos t)^T$ が現れた。また $J_f(\gamma(t)):=(f_x\quad f_y)$ は $f$ のヤコビ行列であるので

$$
\frac{\mathrm{d}}{\mathrm{d}t}f(\cos t,\sin t) = J_f(\gamma(t))\gamma'(t)
$$

と書ける。一般に、 $\mathcal{M}$ がユークリッド空間であれば

$$ \dot{\gamma}(0)f = \mathrm{D}_f(\gamma(0))[\gamma'(0)] $$

が成立し、曲線に沿った方向微分となっている事が分かる。

{{% proposition %}}
2つの $x$ を通る曲線 $\gamma_1,\gamma_2\ (\gamma_1(0)=\gamma_2(0)=x)$ から得られる $x$ での接ベクトルが一致するのは、適当な$x$を含むチャート $(U, \varphi(x))$ について

$$
\left.\frac{\mathrm{d}}{\mathrm{d}t}\varphi(\gamma\_1(t))\right|\_{t=0} =
\left.\frac{\mathrm{d}}{\mathrm{d}t}\varphi(\gamma\_2(t))\right|\_{t=0}
$$
となる時である。

{{% /proposition %}}

接ベクトルというのは $x$ の周りの局所的な性質で決まるので、曲線の選び方には任意性があるが、適当なチャートで座標表示して得られる馴染みのある接ベクトル表現が一致すれば、どちらの曲線を選んでも良い。

{{% definition title="接ベクトル空間" %}}
多様体 $\mathcal{M}$ の点 $x$ における接ベクトルの集合を **接ベクトル空間(tangent space)** といい、 $T_x\mathcal{M}$ と書く。
{{% /definition %}}
