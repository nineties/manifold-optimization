---
title: 多様体
---

[教科書](https://press.princeton.edu/absil)で多様体の定義では、よくある(?)定義と異なって極大アトラスを用いるものになっている。よくある定義では多様体 $M$ の構造をハウスドルフ空間であるなど天下り的に与える事が多いけど、これから多様体と見なして分析しようとしている $M$ の構造が予め与えるというのは確かに違和感がある。教科書の定義では $M$ は単なる集合として導入されて、 $M$ 上のチャートの集合によって構造を入れるというより自然な感じな流れになっている。

ただ、今回の目的は多様体の抽象論的な構成方法ではなくて最適化問題について学ぶ事であるので、以下では一般的な定義を採用して進めていく事にする。

## 多様体の定義

<div class="definition" markdown=1>
$M$を位相空間とする。$M$の開集合 $U$からユークリッド空間 $\mathbb{R}^d$ の開集合$V$ への同相写像 $\varphi:U\rightarrow V$がある時 $(U,\varphi)$を$M$の$d$次元の **チャート(chart)**という。誤解の恐れのない場合には $\varphi$ の事をチャートと呼ぶこともある。

点 $x\in U$ に対して $\varphi(x)\in\mathbb{R}^d$ を $x$ のチャート $\varphi(x)$ における**座標(coordinate)**と言う。
</div>

チャートは $M$ の局所的な様子を、調べやすいユークリッド空間 $\mathbb{R}^d$ に写しとっていて、 $\varphi(U)$ を通して $U$ について調べることが可能になる。

例えば $M$ を地球、 チャートをある一地方の地図だと思うとイメージしやすい。地球そのものを見なくても、地図上である程度のことは把握できる。

<img src="images/chart.png" width="50%">

<div class="definition" markdown=1>
$M$ を位相空間とする。$M$の $d$次元チャートの集合
 $\\{U_\lambda\\}_{\lambda\in\Lambda}$ で

\\[ M=\bigcup_{\lambda\in\Lambda}U_\lambda \\]

となるものを $d$次元 **アトラス(atlas)**という。
</div>

アトラスは地図を集めた地図帳。

<div class="definition" markdown=1>
位相空間 $M$ とその $d$次元アトラス $A$ のペア $(M,A)$ を $d$次元 **多様体(manifold)** という。誤解の恐れがない場合には $M$自身 の事を多様体と呼ぶこともある。
</div>

多様体とは、地図帳がセットになって色々調べることができるようになった位相空間。

<div class="definition" markdown=1>
多様体 $M$ の2つの交わるチャート $(U,\varphi),(V,\psi),U\cap V\neq\emptyset$ に対して

\\[ \psi\circ\varphi^{-1}: \varphi(U\cap V)\rightarrow\psi(U\cap V) \\]
を **座標変換(change of coordinates)**という
</div>

2つの地図に重なっている地域があるならば、一方の地図ともう一方の地図の対応を付けられるということ。

<img src="images/change_of_coordinates.png" width="50%">

$U,V$ は$M$の開集合なので $U\cap V$ も開集合。 $\varphi,\psi$ は同相写像だから $\varphi(U\cap V),\psi(U\cap V)$ も開集合。よって、$\psi\circ\varphi^{-1}$は $\mathbb{R}^d$ の開集合から $\mathbb{R}^d$ の開集合への同相写像になる。

<div class="definition" markdown=1>
多様体 $M$ の任意の座標変換が $C^\alpha$ 級である時これを **$C^\alpha$ 級多様体($C^\alpha$ manifold)** という
</div> 

