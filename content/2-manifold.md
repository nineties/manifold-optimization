---
title: 2. 多様体の定義
section: 2
---

[教科書](https://press.princeton.edu/absil)では、(私が)よく見る定義とは異なり **極大アトラス** を用いて多様体の定義を行なっている。
よくある定義では多様体 $\mathcal{M}$ の位相構造が天下り的に与えられる事が多いが、極大アトラスを用いた定義では $\mathcal{M}$ は単なる集合として導入されて極大アトラスによってその位相構造が自然と定まるという順番になる。

最初はこの定義を見て戸惑ったが、これから謎の空間 $\mathcal{M}$ を多様体と見なして調べようと言う時に、その位相構造が最初から分かっているという前提は強すぎるかもしれない。
極大アトラスを用いる定義はより抽象的で難易度が高いと感じたが、実際に問題を解く上でも$\mathcal{M}$の位相構造を所与とするより便利であるように思う。
このノートでも、教科書の方針に従った定義を採用する。

{{% definition title="チャート" %}}
$\mathcal{M}$を集合とする。$\mathcal{M}$の部分集合 $U$からユークリッド空間 $\mathbb{R}^d$ の開集合$V$ への全単射 $\varphi:U\rightarrow V$がある時 $(U,\varphi)$を$\mathcal{M}$の$d$次元の **チャート(chart)** という。誤解の恐れのない場合には $U$ や $\varphi$ の事を単体でチャートと呼ぶこともある。

点 $x\in U$ に対して $\varphi(x)\in\mathbb{R}^d$ を $x$ のチャート $\varphi$ における **座標(coordinate)** と言う。
{{% /definition %}}

チャートで、$\mathcal{M}$ の局所的な様子をより調べやすい空間であるユークリッド空間 $\mathbb{R}^d$ に写しとる事で、 $\varphi(U)$ を通して $U$ について調べることが可能になる。

これは例えば $\mathcal{M}$ を地球、 チャートをある一地方の地図だと思うとイメージしやすい。地球そのものを直接観察するよりは、地図を観察する方が易しい。

{{< figure src="../images/chart.png" >}}

{{% definition title="チャートの両立" %}}
2つの $d$次元チャート $(U,\varphi),(V,\psi)$ に対して

$$ \psi\circ\varphi^{-1}: \varphi(U\cap V)\rightarrow\psi(U\cap V) $$

を **座標変換(change of coordinates)** という。

$\varphi(U\cap V), \psi(U\cap V)$ がどちらも$\mathbb{R}^d$の開集合であり、$\psi\circ\varphi^{-1}$ が($C^\infty$) 微分同相写像であるとき、2つのチャートは **両立する(compatible)** という。
{{% /definition %}}

写像 $f:\mathbb{R}^m\rightarrow\mathbb{R}^n$ が $C^\infty$ 級であるというのは、

$$ f(x_1,\ldots,x_m)=(f(x_1,\ldots,x_m),\ldots,f(x_1,\ldots,x_m)) $$

の時、各 $f_i$ の $x_1,\ldots,x_m$ での任意の偏微分係数が存在し連続であるということ。$f$ が微分同相であるというのは全単射であり $f$ も $f^{-1}$ も$C^\infty$ 級であるということ。

2つの地図に重なっている地域があるとき、それらが両立するならばその地域について調べるのにどちらの地図を選んでも良いという事を言っている。

{{< figure src="../images/change-of-coordinates.png" >}}

特別な場合として交わらないチャートは常に両立する。($\because$ 空集合は開集合。空集合から空集合への写像は微分同相)

{{% definition title="アトラス" %}}
$\mathcal{M}$ を集合とする。$\mathcal{M}$の $d$次元チャートの集合
 $\\{(U_\lambda,\varphi_\lambda)\\}$ で

$$\mathcal{M}=\bigcup_\lambda U_\lambda$$

であり、任意の2つのチャートが両立するものを
 $d$次元 **アトラス(atlas)** という。
{{% /definition %}}

アトラスは地図を集めた地図帳であり、 $\mathcal{M}$ 全体を覆う。

---

2次元単位球面のアトラスの例:

$S^2=\\{(x,y,z)\|x^2+y^2+z^2=1\\}$ について $U_+=S^2\setminus\\{(0,0,-1)\\},U_-=S^2\setminus\\{(0,0,1)\\}$
とする。$U_+$ は$S^2$の南極一点を除いた集合、$U_-$ は北極一点を除いた集合。
$\varphi_+:U_+\rightarrow \mathbb{R}^2: p\rightarrow\varphi_+(p)$ を、 $p$を$(0,0,-1)$と$p$を通る直線が平面 $z=0$ と交わる点に移す写像とする(南極点から$xy$平面への射影)。同様に $\varphi_-:U_-\rightarrow\mathbb{R}^2$ を北極点からの射影と定義する。このとき $\\{(U_+,\varphi_+),(U_-,\varphi_-)\\}$ は $S^2$ のアトラスとなる。

実際に計算してみると

$$
\varphi_+(x,y,z)=\left(\frac{x}{1+z},\frac{y}{1+z}\right),\quad
\varphi_-(x,y,z)=\left(\frac
{x}{1-z},\frac{y}{1-z}\right) 
$$
となる。これらの逆写像は
$$
\begin{aligned}
\varphi_+^{-1}(u,v)&=\left(\frac{2u}{u^2+v^2+1},\frac{2v}{u^2+v^2+1},-\frac{u^2+v^2-1}{u^2+v^2+1}\right) \\\\ \\\\
\varphi_-^{-1}(u,v)&=\left(\frac{2u}{u^2+v^2+1},\frac{2v}{u^2+v^2+1},\frac{u^2+v^2-1}{u^2+v^2+1}\right)
\end{aligned}
$$

となり、確かに $\varphi_+,\varphi_-$ は全単射で $\mathbb{R}^2$ は開集合だから、これらはチャートである。

次に座標変換について調べるが、まず
$\varphi_+(U_+\cap U_-)=\varphi_-(U_+\cap U_-)=\mathbb{R}\setminus\\{(0,0)\\}$ であって、これはユークリッド空間 $\mathbb{R}^2$ の開集合。($\because$ 一点集合$\\{(0,0)\\}$は閉集合)


座標変換 $\varphi_-\circ\varphi_+^{-1}$ は

$$
\varphi_-\circ\varphi_+^{-1}(u,v)=\left(\frac{u}{u^2+v^2},\frac{v}{u^2+v^2}\right)
$$

となるが、これは $\mathbb{R}\setminus\\{(0,0)\\}$ 上の微分同相写像である。以上より2つのチャートは両立し、$S^2=U_+\cup U_-$ なので $\\{(U_+,\varphi_+),(U_-,\varphi_-)\\}$ は $S^2$ のアトラス。

---
馴染みのない例:

$\mathcal{M}$ を $\mathbb{R}^2$ 内の直線の集合とし、$U$ を $y$ 軸に並行ではない直線の集合、$V$ を $x$ 軸に並行ではない直線の集合とする。つまり

$$
U=\\{y=mx+b\|m,b\in\mathbb{R}\\},
V=\\{x=ny+c\|n,c\in\mathbb{R}\\}
$$

とかける。ここで
$$
\begin{aligned}
\varphi&:U\rightarrow\mathbb{R}^2:\varphi(y=mx+b)=(m,b)\\\\
\psi&:V\rightarrow\mathbb{R}^2:\psi(x=ny+c)=(n,c)\\\\
\end{aligned}
$$
と置くとこれらはチャートになる。$U\cap V$ は水平でも並行でもない直線の集合で $\varphi(U\cap V)=\psi(U\cap V)=\\{(a,b)\|a,b\in\mathbb{R},a\neq 0\\}$ になる。これは $\mathbb{R}^2$ の開集合で $\psi\circ\varphi^{-1}:(m,b)\mapsto(1/m,-b/m)$ は $m\neq 0$ で微分同相。$U\cup V=\mathcal{M}$ だから $\\{(U,\varphi),(V,\psi)\\}$ は$\mathcal{M}$ のアトラス)。

---



一つの $\mathcal{M}$ に対してアトラスの選び方は無数にあるが、それらの間に同値関係を定義する事ができる。すると、今後述べるいろいろな性質について同値なアトラスだったらどれを具体的に選んで使っても良いという形になり便利。

{{% definition title="アトラスの両立" %}}
$\mathcal{M}$ のアトラス $\mathcal{A},\mathcal{B}$ について $\mathcal{A}\cup\mathcal{B}$ も $\mathcal{M}$ のアトラスとなるとき、 $\mathcal{A},\mathcal{B}$ は **両立する(compatible)** といい $\mathcal{A}\sim\mathcal{B}$ と書く。
{{% /definition %}}

アトラスの両立性とは、地図帳を2冊持ってきて、それらを両方同時に使っても不都合が生じないという状況。そして、これは同値関係である。

{{% proposition %}}
アトラスの両立関係は同値関係である。
{{% /proposition %}}

これは直感的には明らかな感じがするけど、証明は結構複雑。

---
証明

任意のアトラスについて
$$\mathcal{A}\sim\mathcal{A}\quad(\text{反射律}) $$
$$\mathcal{A}\sim\mathcal{B}\Rightarrow\mathcal{B}\rightarrow\mathcal{A}\quad(\text{対称律})$$
が成立することは明らかなので、
$$\mathcal{A}\sim\mathcal{B},\mathcal{B}\sim\mathcal{C}\Rightarrow\mathcal{A}\sim\mathcal{C}\quad(\text{推移律})$$
を示せば良い。その為には、$\mathcal{A}\sim\mathcal{B},\mathcal{B}\sim\mathcal{C}$ の時に、任意のチャート $(U,\varphi)\in\mathcal{A},(V,\psi)\in\mathcal{C}$ が両立する事を示せば良い。

それぞれのチャートは, 任意の$(U_\alpha,\varphi_\alpha)\in \mathcal{B}$ と両立するので
$\varphi_\alpha(U\cap U_\alpha),\varphi_\alpha(V\cap U_\alpha)$ は $\mathbb{R}^d$ の開集合。従ってこれらの共通部分

$$
\varphi_\alpha(U\cap U_\alpha)\cap\varphi_\alpha(V\cap U_\alpha) = \varphi_\alpha(U\cap V\cap U_\alpha)
$$

も開集合。($\because$ $f$が全単射ならば $f(A\cap B)=f(A)\cap f(B)$)

よって$\varphi\circ\varphi_\alpha^{-1}$ は同相写像だから

$$
\varphi(U\cap V\cap U_\alpha)=(\varphi\circ\varphi_\alpha^{-1})(\varphi_\alpha(U\cap V\cap U_\alpha))
$$

も $\mathbb{R}^d$ の開集合。よって

$$
\varphi(U\cap V)=\varphi\left(\bigcup_\alpha U\cap V\cap U_\alpha\right) = \bigcup_\alpha\varphi(U\cap V\cap U_\alpha)
$$

も開集合。全く同様にして $\psi(U\cap V)$ も開集合。

あとは座標変換 $\psi\circ\varphi^{-1}:\varphi(U\cap V)\rightarrow\psi(U\cap V)$が微分同相写像である事を示せば良い。任意の $(U_\alpha,\varphi_\alpha)\in \mathcal{B}$ に対して、

$$
\varphi_\alpha\circ\varphi^{-1}:\varphi(U\cap U_\alpha)\rightarrow\varphi_\alpha(U\cap U_\alpha)
$$

は仮定より微分同相写像。これを開集合 $\varphi(U\cap V\cap U_\alpha)$ に制限した

$$
\varphi_\alpha\circ\varphi^{-1}:\varphi(U\cap V\cap U_\alpha)\rightarrow\varphi_\alpha(U\cap V\cap U_\alpha)
$$

も微分同相写像。$\psi\circ\varphi_\alpha^{-1}$ も同様なので、これらの合成

$$
\psi\circ\varphi^{-1}:\varphi(U\cap V\cap U_\alpha)\rightarrow\psi(U\cap V\cap U_\alpha)
$$

も微分同相写像。よって $$\varphi(U\cap V)= \bigcup_\alpha\varphi(U\cap V\cap U_\alpha)$$ であったので
$$
\psi\circ\varphi^{-1}: \varphi(U\cap V)\rightarrow\psi(U\cap V) 
$$
も微分同相写像である。$\square$

---

以上でアトラス $\mathcal{A}$ の同値類 $[\mathcal{A}]=\\{\mathcal{B}|\mathcal{B}\sim\mathcal{A}\\}$ を考える事ができるようになる。
アトラスの同値類を用いて多様体を定義するという流儀もあるようだけど、ここでは極大アトラスを導入する。何故かというと、この後定義するハウスドルフ性や第二可算性に関して、極大アトラスを用いた方が(多分)シンプルに述べられるから。

{{% definition title="極大アトラス" %}}
アトラス $\mathcal{A}$ と両立するアトラス全ての合併を $\mathcal{A}$の **極大アトラス(maximal atlas)** といい、$\mathcal{A}^+$ と書く。
{{% /definition %}}

任意のアトラスについて、その極大アトラスが一意に存在する。$\mathcal{A}^+$ には非常に多くのチャートが含まれるが、以下の事実は良く使う。

{{% proposition label="prop.subchart-is-chart" %}}
チャート $(U, \varphi)\in\mathcal{A}$ の部分集合 $V\subset U$ について $\varphi(V)$ が $\mathbb{R}^d$ の開集合ならば、 $(V,\varphi\|_V)\in\mathcal{A}^+$
{{% /proposition %}}

これは$U,V$ の間の座標変換が恒等写像になる事から明らか。地図の一部にだけ注目しても地図である事には変わらないし、他の地図との座標変換も変わらないという事。全く同じだが、次の形で用いることも多い。

{{% proposition label="prop.intersection-is-chart" %}}
集合 $\mathcal{M}$ のチャート $(U,\varphi)\in\mathcal{A}$ と 部分集合 $V\subset \mathcal{M}$ について $\varphi(U\cap V)$ が $\mathbb{R}^d$ の開集合ならば、 $(U\cap V,\varphi\|_{U\cap V})\in\mathcal{A}^+$
{{% /proposition %}}

以上で多様体の定義に必要な最低限の道具は揃ったが、実用上2つの条件を加える。1つは $\mathcal{M}$ が可算個のチャートで覆えるということ、もう一つはハウスドルフ性である。
これらを仮定すると、後ほど導入される極大アトラスの定める位相によって $\mathcal{M}$ が第二可算かつハウスドルフになる事が言える。

{{% definition title="多様体" label="def.manifold" %}}
集合 $\mathcal{M}$ と極大アトラス $\mathcal{A}^+=\\{(U\_\alpha,\varphi\_\alpha)\\}$ が以下を満たすとき、 $(\mathcal{M},\mathcal{A}^+)$ を **$d$次元多様体($d$-dimentional manifold)** という。誤解の恐れの無い場合は $\mathcal{M}$ 自身を多様体と呼ぶ。また $\mathcal{A}^+$ を $\mathcal{M}$ の **微分構造(differential structure)** という。

**ハウスドルフ性(Hausdorff condition)**

任意の異なる点 $x,y\in \mathcal{M},x\neq y$ に対して、これらを含む交わらないチャート,すなわち $(U,\varphi),(V,\psi)\in \mathcal{A}^+$ で$x\in U,y\in V$ かつ $U\cap V=\emptyset$であるものが存在する。

**可算被覆をもつ(Countability condition)**

$\mathcal{M}$ は $\mathcal{A}^+$ の可算個のチャートで覆うことができる。つまり、$U_{\alpha_1},U_{\alpha_2},\ldots$ が存在して $ \mathcal{M}=\bigcup_iU_{\alpha_i}$ と書ける。

{{% /definition %}}

ある集合と極大アトラスがハウスドルフ性を満たすか調べる為には、以下の補題が役に立つ。

{{% lemma label="lem.hausdorff" %}}
$\mathcal{M}$ を集合、 $\mathcal{A}^+$ を極大アトラスとする。
$\mathcal{M}$ の異なる2点 $x,y$ がある1つのチャート $(U,\varphi)\in \mathcal{A}^+$ に含まれるならば、これらを分離する $U$ に含まれるチャートが存在する。

すなわち、あるチャート $U_\alpha,U_\beta\subset U$ が存在して $x\in U_\alpha,y\in U_\beta,U_\alpha\cap U_\beta=\emptyset$
{{% /lemma %}}

$\varphi$ は全単射だから $x\neq y$ の時、$\varphi(x)\neq\varphi(y)$ である。よって $\mathbb{R}^d$ はハウスドルフ空間だから $\varphi(x),\varphi(y)$ を分離する開集合で $\varphi(U)$ に含まれる物を選ぶ事ができる。これらの $\varphi$ での逆像を $U_\alpha,U_\beta$ とすれば $U_\alpha,U_\beta\subset U$ であって $\varphi$ は全単射だから $U_\alpha\cap U_\beta=\emptyset$ となる。それぞれのチャートの写像は $\varphi$ を $U_\alpha,U_\beta$ に制限したものをとれば良い。$\square$

つまり、一つの地図の中に限って見ればハウスドルフ性は自然に成立するということなので、ハウスドルフ性について確認するときは2点が異なるチャートの点である時だけを調べれば良い。

---

ここでよく使うことになりそうな多様体の例を挙げる。

{{% example title="$n$次元球面" label="ex.n-sphere"%}}
$$
S^n=\\{\mathbf{x}\|\mathbf{x}\in\mathbb{R}^{n+1},||\mathbf{x}||=1\\}
$$

を **$n$ 次元球面($n$-sphere)** という。
$U\_\pm$ を $S^n$ から $(\mp 1,0,\ldots)$ を除いた集合とし, 写像 $\varphi\_\pm :U\_\pm\rightarrow\mathbb{R}^n$ を
$$
\varphi\_\pm(x_0,x_1,\ldots,x_n) = \frac{1}{1\pm x_0}(x_1,\ldots,x_n)
$$
とすると $(U_\pm,\varphi_\pm)$ はチャートである。また、 $\mathcal{A}=\\{(U_+,\varphi_+),(U_-,\varphi_-)\\}$ はアトラスであり、 $(S^n,\mathcal{A}^+)$ は$n$次元多様体である。
{{% /example %}}


$\varphi_\pm$ がチャートである事と、$\mathcal{A}$ がアトラスである事の証明は上でやった $S^2$ の場合とほとんど同じなので省略し、極大アトラス $\mathcal{A}^+$ をとると $(S^n,\mathcal{A}^+)$ が多様体になる事を示す。

まず $S^n=U_+\cup U_-$ だから可算被覆を持つ事は明らか。続いて、ハウスドルフ性についてだが、{{< ref lem.hausdorff >}}より2点が同じチャートに含まれる場合には成立するので、2点が $(1,0,\ldots)$ と $(-1,0,\ldots)$ である場合のみ考えれば良い。

$V_+$ を $U_+$ の $x_0>0$ の部分、 $V_-$ を $U_-$ の $x_0<0$ の部分とすれば

$$\varphi_+(V_+)=\varphi_-(V_-)=\\{\mathbf{x}\|\mathbf{x}\in\mathbb{R}^n,\|\|\mathbf{x}\|\|>1\\}$$

となって、これらは $\mathbb{R}^n$ の開集合($\because$ 閉球体の補集合)だから、$\varphi_\pm$ のこれらへの制限は $S^n$ のチャートになる。
そして $V_+\cap V_-=\emptyset$ だから、これらは $(\pm 1,0,\ldots)$ を分離する。以上より $(S^n,\mathcal{A}^+)$ はハウスドルフ性を満たす。

よって $(S^n,\mathcal{A}^+)$ は $n$ 次元多様体である。$\square$

{{% example title="ベクトル空間" %}}
$V$ が $n$次元ベクトル空間であるならば、任意の基底 $e_1,\ldots,e_n$ 上での成分表示

$$ \varphi:V\rightarrow\mathbb{R}^n:x\mapsto(x_1,\ldots,x_n) $$

がこれ1つでアトラスとなり 、 $V$ は $n$ 次元多様体となる。
{{% /example %}}

{{% example title="行列の集合" %}}
$n\times p$ 実行列の集合 $\mathbb{R}^{n\times p}$ は
$$\varphi:\mathbb{R}^{n\times p}\rightarrow\mathbb{R}^{np}:X\mapsto\mathrm{vec}(X)$$
(ただし $\mathrm{vec}(X)$ は $X$ の各列を縦に繋げたベクトル)

とすると $\varphi$ 1つでアトラスとなり $\mathbb{R}^{n\times p}$ は $np$次元多様体となる。
{{% /example %}}

{{% example title="一般線型群" %}}
$n$次実正則行列の集合 $$GL_n=\\{X\in\mathbb{R}^{n\times n}\|\det X\neq 0\\} $$
は行列の積によって群となる。これを **一般線型群(general linear group)** という。

写像
$$\varphi:GL_n\rightarrow\mathbb{R}^{n^2}: X\mapsto\mathrm{vec}(X)$$
を考えると $\mathcal{A}=\\{(GL_n,\varphi)\\}$ がアトラスとなり、 $(GL_n,\mathcal{A}^+)$ は $n^2$次元多様体となる。
{{% /example %}}

まず $\varphi(GL_n)$ が開集合である事を示す。補集合を考えると、
$$
\begin{aligned}
\mathbf{x}\in\mathbb{R}^{n^2}\setminus\varphi(GL_n)&\Leftrightarrow\det\circ\mathrm{vec}^{-1}(\mathbf{x})=0 \\\\
&\Leftrightarrow\mathbf{x}\in(\det\circ\mathrm{vec}^{-1})^{-1}(\\{0\\})
\end{aligned}$$

ここで $\det\circ\mathrm{vec}^{-1}:\mathbb{R}^{n^2}\rightarrow\mathbb{R}$ はベクトルの成分の加減乗算のみで定義されるので連続。そして一点集合 $\\{0\\}$ は閉集合であるので、その逆像である $\mathbb{R}^{n^2}\setminus\varphi(GL_n)$ も閉集合。よって $GL_n$ は開集合。

また $\mathrm{vec}$ は全単射だから $(GL_n,\varphi)$ はチャートである。$GL_n$ 全体が一つのチャートで覆われるので、可算被覆を持つことは明らか。ハウスドルフ性も{{< ref lem.hausdorff >}}より明らか。

---
$GL_n$ のような群構造を持つ多様体を **リー群(Lie group)** という。

同じようにして特殊線型群 $SL_n=\\{X\in\mathbb{R}^{n\times n}\|\det X=1\\}$ なども多様体になるが、 $GL_n$ と同じようにチャートを与える事によって直接示すのは大変なので、いくつか定理を示した後にやる。

{{% example title="ノンコンパクトシュティーフェル多様体" %}}
$\mathbb{R}^{n\times p}\_\ast, (p\leq n)$ を各列が一次独立な行列の集合(フルランクの行列の集合)とする。これは
$$\mathbb{R}^{n\times p}\_\ast = \\{X\in\mathbb{R}^{n\times p}\mid\det(X^TX)\neq 0\\}$$
と書く事ができる。この集合はチャート
$$\varphi:\mathbb{R}^{n\times p}\rightarrow\mathbb{R}^{np}:X\mapsto\mathrm{vec}(X)$$
によって$np$次元多様体となる。これを **ノンコンパクトシュティーフェル多様体(noncompact Stiefel manifold)** という。
{{% /example %}}

特別な場合として、$p=1$ のときはユークリッド空間 $\mathbb{R}^n$ から原点を除いた空間 $\mathbb{R}^n\_\ast$ となる。 $p=n$ のときは一般線型群となる。

---

ハウスドルフ性を満たさない例を挙げる。

{{% example title="2直線を張り合わせた空間" label="ex.y-shape-space" %}}

空間 $\mathbb{R}\times \\{0,1\\}$ において $x<0$ の部分で $(x,0)$ と $(x,1)$ を同一視して得られる商空間を $\mathcal{M}$ とする。

$\pi:X\rightarrow\mathcal{M}$ を商写像とする。$U=\pi(\mathbb{R}\times\\{0\\}), V=\pi(\mathbb{R}\times\\{1\\})$ とし、

$$
\begin{aligned}
\varphi:U \rightarrow\mathbb{R}: (x,0)\mapsto x \\\\
\psi:V \rightarrow\mathbb{R}: (x,1)\mapsto x \\\\
\end{aligned}
$$

とおくと $\mathcal{A}=\\{(U,\varphi),(V,\psi)\\}$ は $\mathcal{M}$ のアトラス。
{{% /example %}}

$\mathcal{M}$ は2つの直線を張り合わせた空間で、 $\varphi,\psi$ は張り合わせる前の直線を取り出すもの。この時 $(\mathcal{M},\mathcal{A}^+)$ はハウスドルフ性を満たさない。
具体的には異なる2点 $(0,0),(0,1)\in\mathcal{M}$ について条件を満たすチャートは存在しない。
