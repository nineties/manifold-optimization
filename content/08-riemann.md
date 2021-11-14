---
title: 8. リーマン多様体、勾配
section: 8
---

前節までで多様体上で定義された滑らかな関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ の方向微分は計算できるようになったが、最適化アルゴリズムを実行する為には **勾配(gradient)** が必要である。そして、勾配を定義する為には多様体に **リーマン計量(Riemannian metric)** という構造を入れる必要がある。

勾配を定めるのに何故リーマン計量が必要なのか戸惑うかもしれない(私は最初は戸惑った)。接ベクトル空間 $T_x\mathcal{M}$ を定めることができて各接ベクトル $v\in T_x\mathcal{M}$ に沿った方向微分を計算できるのに、何故勾配を定める事ができないのか？という事である。

そもそも勾配とはなんであるかというと、ベクトル解析における概念では $f$ の変化率が最大となる方向を向いていて、ノルムがその変化率であるようなベクトル指すのだった。多様体の上での勾配はこれを一般化した概念としたいが、接ベクトル $v\in T_x\mathcal{M}$ の **長さ** が与えられていないので、変化率が最大つまり **同じ距離だけ進んだ時** に $f$ が最も大きく変化する方向を定める事ができない。リーマン計量を入れれば、ベクトルの長さなどの幾何学的性質を多様体の上で定義する事が可能になる為、勾配も定義する事が可能になる。

{{% definition title="内積" %}}
実ベクトル空間 $V$ に対して定められた写像 $\langle\cdot ,\cdot\rangle:V\times V\rightarrow\mathbb{R}$
が以下の性質を満たすとき、これを **内積(inner product)** という。

任意の $u,v,w\in V,a\in\mathbb{R}$ に対して

- 対称性: $\langle u,v\rangle = \langle v,u\rangle$
- 第一引数についての線型性: $\langle au+v, w\rangle =a\langle u, w\rangle +\langle v, w\rangle$
- 正定値性: $u\neq 0\Rightarrow \langle u, u\rangle > 0$
{{% /definition %}}

第二引数についての線型性は対称性と第一引数についての線型性より導かれる。
$\langle 0, 0\rangle =\langle 0+0, 0\rangle =\langle 0, 0\rangle + \langle 0, 0\rangle $ より $\langle 0, 0\rangle =0$ なので $\langle u, u\rangle \geq 0$ である事と、非退化性 $\langle u, u\rangle =0\Rightarrow u=0$ も得られる。

よく使う内積は以下。

{{% example title="ユークリッド空間の標準内積" %}}
$$ \langle x, y\rangle = x^T y $$
{{% /example %}}

{{% example title="$\mathbb{R}^{n\times p}$の標準内積" %}}
$$ \langle X, Y\rangle = \mathrm{tr}(X^TY) $$
{{% /example %}}

$ X=[x_1\cdots x_p],Y=[y_1\cdots y_p]$ とすると
$$\mathrm{tr}(X^TY)=x_1^Ty_1 + \cdots + x_p^Ty_p $$
であるので、これは $X,Y$ の列ベクトル毎の内積の和になっている。

{{% definition title="リーマン多様体" %}}
多様体 $\mathcal{M}$ の各点 $x$ の接ベクトル空間に内積
$$g_x:T_x\mathcal{M}\times T_x\mathcal{M}\rightarrow\mathbb{R}$$
が定められており、任意のベクトル場 $U,V$ について写像
$$ \mathcal{M}\ni x\mapsto g_x(U_x,V_x)\in\mathbb{R}$$
が滑らかであるとき、対応 $g:x\mapsto g_x$ を **リーマン計量(Riemannian metric)** という。リーマン計量の備わった多様体 $(\mathcal{M},g)$ を  **リーマン多様体(Riemannian manifold)** という。
{{% /definition %}}

文脈から誤解の恐れがない場合には $g$ を省略して「リーマン多様体 $\mathcal{M}$」と呼ぶ事がある。

また $g_x(u,v)$ の代わりに $\langle u, v\rangle _x$ や、$x$ を省略して $\langle u,v\rangle$ と書く。

さて、内積が定まったのでベクトル $u\in T_x\mathcal{M}$ に対して、そのノルムを定める事が出来る。

{{% definition title="ノルム" %}}
$$ ||u|| = \sqrt{\langle u, u\rangle} $$
をベクトル $u$ の **ノルム(norm)** という。
{{% /definition %}}

あるチャートを選ぶと、接ベクトルは基底
$$ \left(\frac{\partial}{\partial x_i}\right)_x$$ 
で成分表示できるので、リーマン計量 $g_x$ は行列 $G_x$ 

$$ (G_x)_{ij} := \left\langle \left(\frac{\partial}{\partial x_i}\right)_x,\left(\frac{\partial}{\partial x_j}\right)_x \right\rangle $$

によって定まる。これが内積を定める必要十分条件は $G_x$ が正定値対称行列である事である。接ベクトル $u,v\in T_x\mathcal{M}$ の標準基底に対する成分を $\mathbf{u},\mathbf{v}\in\mathbb{R}^m$ とすれば

$$\langle u, v \rangle = \mathbf{u}^TG_x\mathbf{v} $$

となる。

このように一つのチャートの中だけであればリーマン計量は正定値対称行列を用いて簡単に定める事が出来るが、$\mathcal{M}$ 全体についての計量にはなっていない。ここで、以下の命題が成り立つ。

{{% proposition %}}
多様体 $\mathcal{M}$ には少なくとも一つのリーマン計量を定める事が出来る。
{{% /proposition %}}

第二可算性、ハウスドルフ性が嬉しい命題がここで登場した。

$\mathcal{M}$ が第二可算かつハウスドルフならば **1の分割(partition of unity)** というものが存在する事が示せて、これを使って任意の多様体にリーマン計量を定める事が出来る。詳しい証明を書くのは重たい上、本筋から外れてしまうが、気持ちを説明する。

まず $\mathcal{M}$ の適当なアトラス $\mathcal{A}=\\{(U_\alpha,\varphi_\alpha)\\}$ を取ると、上で示したように各チャートの中ではリーマン計量の存在を示す事が簡単に出来る。例えば

$$ G_x = I_m $$

とすれば良い。

問題はチャートとチャートが重なっている部分である。そこで、1の分割というものを利用してチャートが重なっている部分の計量をブレンドしていく。1の分割というのはこのブレンドの為の重み付けを表す関数族のこと。具体的には、各チャート $U_\alpha$ に備え付けられた滑らかな関数 $\rho_\alpha:U_\alpha\rightarrow[0,1]$ であって、 $U_\alpha$ の外では $\rho_\alpha(x)=0$ になり、各点 $x$ について $\rho_\alpha(x) > 0$ となるものは有限個しかなく、全ての点で $\sum_\alpha \rho_\alpha(x) = 1$ となるようなもの。これを使って各チャート毎に定められた計量 $g_{\alpha,x}$ をブレンドして
$$ g_x=\sum_\alpha\rho_\alpha(x) g_{\alpha,x}\quad (\text{ただし $x\not\in U_\alpha$ の時は $g_{\alpha,x}=0$})$$
とすれば $\mathcal{M}$ 全体に対するリーマン計量を作れる。

{{% definition title="曲線の長さ" %}}
$\mathcal{M}$ 上の曲線 $\gamma: [a,b]\rightarrow\mathcal{M}$ に対して

$$ L(\gamma) = \int_a^b ||\dot{\gamma}(t)||\mathrm{d} t $$

を曲線 $\gamma$ の **長さ(length)** という。
{{% /definition %}}

実はこれまで $\dot{\gamma}(0)$ は定義したが $\dot{\gamma}(t)$ は現れなかった。が、全く同様で写像

$$\dot{\gamma}(t):C_x(\mathcal{M})\rightarrow\mathbb{R}:f\mapsto\frac{\mathrm{d}(f\circ\gamma)}{\mathrm{d}t}(t) $$

の事であって、これは接ベクトル空間 $T_{\gamma(t)}\mathcal{M}$ の元になる。

{{% definition title="リーマン距離" %}}
連結なリーマン多様体 $\mathcal{M}$ 上の点 $x,y\in\mathcal{M}$ に対して

$$ d(x,y) := \inf\\{L(\gamma)\mid \text{$\gamma$は$x,y$を結ぶ曲線}\\}$$

を **リーマン距離(Riemannian distance)** という。
{{% /definition %}}

2点間を結ぶ曲線で最短のものの長さを距離と呼ぶ事にしたわけだが、これは実際に距離の公理を満たす。

{{% proposition %}}
リーマン多様体はリーマン距離によって距離空間となる。すなわちリーマン距離 $d$ は距離の公理を満たす。

- 非退化性: $d(x,y)=0\Leftrightarrow x=y$
- 対称性: $d(x,y)=d(y,x)$
- 三角不等式: $d(x,y) + d(y,z) \geq d(x,z)$
{{% /proposition %}}

これは計量空間がノルムによって距離空間となるという話とは全然異なるものなので注意。

{{% definition title="勾配" %}}
リーマン多様体 $\mathcal{M}$ 上で定義された滑らかな関数 $f:\mathcal{M}\rightarrow\mathbb{R}$ の点 $x$ における
**勾配(gradient)** $\mathrm{grad} f(x)$ とは $x$ における接ベクトルであって、任意の $h\in T_x\mathcal{M}$ に対して

$$ \langle \mathrm{grad} f(x), h\rangle = \mathrm{D}f(x)[h] $$

となるものである。

$\mathrm{grad} f(x) = 0$ であるような点 $x$ を $f$ の **停留点(Stationary point)** という。
{{% /definition %}}

$x$ の周りのチャートにおける成分表示では

$$ \mathrm{grad} f(x) = G_x^{-1}\frac{\partial}{\partial x}f(x)=G_x^{-1}\left(
\frac{\partial f}{\partial x_1}(x),\ldots,
\frac{\partial f}{\partial x_m}(x)
\right)^T$$

となる。実際に計算してみると、この座標系で $h=(h_1,\ldots,h_m)$ とおくと

$$
\langle\mathrm{grad} f(x),h\rangle = h^TG_x G_x^{-1}\frac{\partial}{\partial x}f(x) 
= h^T\frac{\partial}{\partial x}f(x)
= \sum_i h_i\frac{\partial f}{\partial x_i}(x)
$$

よってチャートを $\varphi$、$h$ に対応する適当な曲線を $\gamma$ とすると、各成分は

$$
h_i = \frac{\mathrm{d}(\varphi_i\circ\gamma)}{\mathrm{d}t}(0),\quad
\frac{\partial f}{\partial x_i}(x) =
\left(\frac{\partial (f\circ\varphi^{-1})}{\partial x_i}\right)_x
$$

であったので

$$\langle\mathrm{grad} f(x),h\rangle =
\sum_i
 \frac{\mathrm{d}(\varphi_i\circ\gamma)}{\mathrm{d}t}(0)
\left(\frac{\partial (f\circ\varphi^{-1})}{\partial x_i}\right)_x = \frac{\mathrm{d}(f\circ\gamma)}{\mathrm{d}t}(0) = \mathrm{D}f(x)[h]
$$

となる。


{{% example title="ユークリッド空間における勾配" %}}
ユークリッド空間 $\mathbb{R}^m$ 上の滑らかな関数 $f:\mathbb{R}^m\rightarrow\mathbb{R}$の勾配は
$$\mathrm{grad} f(x) = (f_{x_1}(x),\ldots,f_{x_m}(x))^T $$
{{% /example %}}

{{% example title="$\mathbb{R}^{n\times p}$ における勾配" %}}
ベクトル空間 $\mathbb{R}^{n\times p}$ 上の滑らかな関数 $f:\mathbb{R}^{n\times p}\rightarrow\mathbb{R}$の勾配は変数を $x_{ij}=X_{ij}$ とおいた時

$$ \mathrm{grad} f(X) = \begin{pmatrix}
f_{x_{11}}(X) & \cdots & f_{x_{1p}}(X) \\\\
\vdots & \ddots & \vdots \\\\
f_{x_{n1}}(X) & \cdots & f_{x_{np}}(X) \\\\
\end{pmatrix} $$
{{% /example %}}

こうして求めた勾配が、実際に $f$ の変化率を最大化する方向を向いた、ノルムが変化率のベクトルである事が示せる。ここで変化率とはノルムが1のベクトルに対する方向微分のこととする。

{{% proposition %}}
ノルムが$1$の接ベクトル $v\in T_x\mathcal{M},||v||=1$ で、方向微分 $\mathrm{D}f(x)[v]$ が最大となるものは
$$ v = \frac{\mathrm{grad} f(x)}{||\mathrm{grad} f(x)||} $$
である。また、この時の最大値は $||\mathrm{grad} f(x)||$ と一致する。 
{{% /proposition %}}

[証明]

コーシー・シュワルツの不等式

$$ \langle \mathrm{grad} f(x), v\rangle \leq ||\mathrm{grad} f(x) ||\ ||v|| $$

と $||v||=1$ より

$$ \mathrm{D}f(x)[v] \leq ||\mathrm{grad} f(x) || $$

等号が成立するのは $\alpha\in\mathbb{R}$ が存在して $v=\alpha \mathrm{grad} f(x)$ と表される場合であるから、これと $||v||=1$ より

$$ v = \frac{\mathrm{grad} f(x)}{||\mathrm{grad} f(x)||} $$

の時に $\mathrm{D}f(x)[v]$ は最大となり、最大値は $||\mathrm{grad} f(x)||$ である。 $\square$

---

$m$ 次元リーマン多様体 $\mathcal{M}$ の $n$ 次元部分多様体 $\mathcal{N}$ に対して $\mathcal{M}$ のリーマン計量から自然に定まる計量を入れる事ができる。 すなわち $\mathcal{M}$ の計量 $g$ をそのまま利用すれば良い。

この時 $T_x\mathcal{N}$ は $T_x\mathcal{M}$ の部分空間であって内積が定められているので、その直交補空間

$$ (T_x\mathcal{N})^\bot = \\{u\in T_x\mathcal{M}\mid \langle u,v\rangle = 0, \forall v\in T_x\mathcal{N}\\}$$

が存在して

$$  T_x\mathcal{M} = T_x\mathcal{N}\oplus (T_x\mathcal{N})^\bot$$

と分解する事が出来る。このような分解を **直交直和分解(orthogonal direct sum decomposition)** という。また $(T_x\mathcal{N})^\bot$ を **法線ベクトル空間(normal vector space)** という。(前節で登場した水平空間 $\mathcal{H}_x$ と似ているがあちらでは直交性は要求していない。というか内積が与えられていない。)

任意のベクトル $u\in T_x\mathcal{M}$ は各空間に含まれる成分に一意に分解する事が出来る。

$$ u=u_V + u_H,\quad u_V\in T_x\mathcal{N},u_H\in (T_x\mathcal{N})^\bot$$

この時、 $u$ から各成分を取り出す線型写像

$$P_x:T_x\mathcal{M}\rightarrow T_x\mathcal{N}: u\mapsto u_V$$
$$P^\bot_x:T_x\mathcal{M}\rightarrow (T_x\mathcal{N})^\bot: u\mapsto u_H$$
をそれぞれの空間への **直交射影(orthogonal projection)** という。 そして、部分空間 $\mathcal{N}$ の点 $x$ における勾配($\mathrm{grad}\_\mathcal{N}f(x)$)は $\mathcal{M}$ における勾配($\mathrm{grad}_\mathcal{M}f(x)$)の $T_x\mathcal{N}$ への直交射影を取れば得られる。すなわち

$$\mathrm{grad}\_\mathcal{N}f(x) = P_x(\mathrm{grad}\_\mathcal{M}f(x)) $$

{{% example title="$n$次元球面" %}}
$n$次元球面 $S^n = \\{x\in\mathbb{R}^{n+1}\mid ||x||=1\\}$ にユークリッド空間 $\mathbb{R}^{n+1}$ の標準内積によってリーマン計量
$$ \langle x,y \rangle = x^Ty $$
を定めたもの。
{{% /example %}}

(リーマン計量の与え方は様々なので、これはあくまで一つの例)

$$ T_x S^n = \\{z\in\mathbb{R}^{n+1}\mid x^Tz=0\\} $$

であったので、法線ベクトル空間は

$$ (T_x S^n)^\bot = \\{ \alpha x \mid \alpha\in\mathbb{R}\\} = x\mathbb{R}$$

となる。また、直交射影は行列

$$P_x = I-xx^T,\quad P^\bot_x = xx^T$$

によって表され、勾配は
$$\mathrm{grad} f(x) = (I-xx^T)\left(f_{x_1}(x),\ldots,f_{x_{n+1}}(x)\right)^T $$
となる。

{{% example title="シュティーフェル多様体" %}}

$$\mathrm{St}(p,n)=\\{X\in\mathbb{R}^{n\times p}\mid X^TX = I_p\\}\quad(p\leq n)$$

に $\mathbb{R}^{n\times p}$ の標準内積によってリーマン計量

$$\langle X, Y \rangle = \mathrm{tr}(X^TY) $$

を定めたもの。
{{% /example %}}

$$T_X\mathrm{St}(p,n)=\\{X\Omega+X_\bot K \mid \Omega^T=-\Omega, K \in\mathbb{R}^{(n-p)\times p} \\}$$

であったので $St(p,n)$ の $X$ での接ベクトルは $ U=X\Omega + X_\bot K$ と書ける。これと $T_X\mathbb{R}^{n\times p}\simeq\mathbb{R}^{n\times p}$ のベクトル $V$ の内積は

$$ \langle U,V\rangle = \mathrm{tr}(U^TV) = \mathrm{tr}(\Omega^TX^TY)+\mathrm{tr}(K^TX_\bot^TY)$$

となる。これが任意の $U$ に対して $0$ になる為にはまず $X_\bot^TY=0$ となる事が必要で、その為には $Y=XS$ と表せる事が必要十分条件である($\because \mathrm{span}(Y)\subset\mathrm{span}(X_\bot)^\bot=\mathrm{span}(X)$であれば良いから)

すると $\langle U,V \rangle = \mathrm{tr}(\Omega^TS) $ となるが $\Omega^T$ は歪対称行列であるのでこれが、これが任意の $\Omega$ に対して $0$ となる必要十分条件は $S$ が対称行列である事。
よって$T_X\mathrm{St}(p,n)$ の法線ベクトル空間は

$$ (T_X\mathrm{St}(p,n))^\bot = \\{XS\mid S\in\mathrm{Sym}_p\\} $$

となる。$V\in\mathbb{R}^{n\times p}$ の直交分解は、

$$\mathrm{sym}(A)=\frac{A+A^T}{2},\mathrm{skew}(A)=\frac{A-A^T}{2}$$ 

とおくと

$$ \begin{aligned}
P_X(V) &= (I-XX^T)V+X\mathrm{skew}(X^TV) \\\\
P^\bot_X(V) &= X\mathrm{sym}(X^TV)
\end{aligned} $$
となる。実際に計算してみると $\mathrm{sym}(A)+\mathrm{skew}(A)=A$ であるから
$$P_X(V)+P^\bot_X(V) = (I-XX^T)V+XX^TV=V$$
であり、内積を計算すると

$$ \langle P^\bot_X(V)^T, P_X(V)\rangle =\mathrm{tr}(\mathrm{sym}(X^TV)\mathrm{skew}(X^TV))=0$$

となって確かに直交する。

{{% example title="直交群" %}}
$$ O_n = \\{X\in\mathbb{R}^{n\times n}\mid X^TX=I \\\}$$
に $\mathbb{R}^{n\times n}$ の標準内積によってリーマン計量
$$\langle X,Y \rangle = \mathrm{tr}(X^TY) $$
を定めたもの。
{{% /example %}}

$O_n = \mathrm{St}(n,n)$ であるので

$$ 
T_XO_n = X\mathrm{Skew}_n,\quad (T_XO_n)^\bot = X\mathrm{Sym}_n
$$
$$ P_X(V) = X\mathrm{skew}(X^TV),\quad
P^\bot_X(V) = X\mathrm{sym}(X^TV)
$$

となる。

---

リーマン多様体$(\mathcal{M},g)$ の商多様体 $\mathcal{M}/{\sim}$ のリーマン計量を $g$ から導出する事を考える。

自然な全射 $\pi:\mathcal{M}\rightarrow\mathcal{M}/{\sim}$ による同値類 $[x]\in\mathcal{M}/{\sim}$ の逆像 $\pi^{-1}([x])$ の点 $x$ での接ベクトル空間

$$ \mathcal{V}_x = T_x\pi^{-1}([x]) $$

を点 $x$ の垂直空間というのだった。前節ではこれの補空間として水平空間を定義したが、今回は $\mathcal{M}$ に内積が定められている為、直交する補空間を取ることが出来る。

$$ \mathcal{H}_x = \mathcal{V}_x^\bot = \\{u\in T_x\mathcal{M}\mid \langle u,v \rangle = 0, \forall v \in\mathcal{V}_x\\}$$

そこで $u,v\in T_{[x]}(\mathcal{M}/{\sim})$ の $\mathcal{H}_x$ への水平リフトを $\bar{u},\bar{v}$ とした時、 $u,v$ の内積を $T_x\mathcal{M}$ における $\bar{u},\bar{v}$ の内積によって定めたい。

$$ g_{[x]}(u,v) = g_x(\bar{u},\bar{v}) $$

これは一般にはリーマン計量には **ならない**。というのは右辺が $x$ に依存する為 well-defined ではないから。右辺が代表元 $x$ の選び方に寄らないときは、これがリーマン計量を定め $\mathcal{M}/{\sim}$ はリーマン多様体となる。このような条件を満たす $\pi$ を **リーマン沈め込み (Riemannian submersion)** という。

$\pi$ がリーマン沈め込みであるならば、滑らかな関数 $f:\mathcal{M}/{\sim}\rightarrow\mathbb{R}$ に対して$\mathrm{grad} (f\circ\pi)(x)$ が $\mathrm{grad} f([x])$ の水平リフトとなる。つまり

$$\mathrm{grad} f([x]) = \mathrm{D}{\pi}(x)[\mathrm{grad} (f\circ\pi)(x)]$$

となる。


{{% example title="実射影空間" %}}
$\mathbb{RP}^{n-1}$ の各点 $[x]$ での接ベクトル $u,v$ の内積を、それらの点 $x$ での $\mathbb{R}^n_\ast$ へのリフト $u_x,v_x$ を用いて

$$ \langle u, v \rangle_{[x]} = \frac{u_x^Tv_x}{||x||^2} $$

と定めると、自然な全射 $\pi:\mathbb{R}^n_\ast\rightarrow\mathbb{RP}^{n-1}$ はリーマン沈め込みとなる。
{{% /example %}}

$x\sim y$ ならばある $\alpha\in\mathbb{R}$ が存在して $y=\alpha x$ と書ける。この時 $$ u_{\alpha x}=\alpha u_x, v_{\alpha x}=\alpha v_x$$ であったから

$$\frac{u_y^Tv_u}{||y||^2} = \frac{u\_{\alpha x}^Tv\_{\alpha x}}{||\alpha x||^2} = \frac{\alpha^2 u_x^Tv_x}{||\alpha x||^2}=\frac{u_x^Tv_x}{||x||^2}$$

よって $\langle u, v \rangle_{[x]}$ は代表元の選び方によらず定まり、 $\pi$ はリーマン沈め込みとなる。

これをグラスマン多様体に一般化すると以下のようになる。

{{% example title="グラスマン多様体" %}}
$\mathrm{Grass}(p,n)$ の各点 $[X]$ での接ベクトル $U,V$ の内積を、それらの点 $X$ での $\mathbb{R}^{n\times p}\_\ast$ へのリフト $U_X,V_X$ を用いて

$$ \langle U,V \rangle_{[X]} = \mathrm{tr}((X^TX)^{-1}U^TV) $$
と定めると、自然な全射 $\pi:\mathbb{R}^{n\times p}_\ast\rightarrow\mathrm{Grass}(p,n)$ はリーマン沈め込みとなる。
{{% /example %}}
