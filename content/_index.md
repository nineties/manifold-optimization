---
title: Manifold Optimization
---

Computer Vision、ロボットの制御、機械学習モデルのパラメータ推定など様々な場面で登場する多様体上での最適化の理論とアルゴリズムについて勉強した際のノートです。
日本語文献が少ないように思ったので、他の人の役に立てばと思い公開して書きます。

このノートでは、基本的には

- [Optimization Algorithms on Matrix Manifolds](https://press.princeton.edu/absil)

を読み進めながら、分からなかったところを補いながら書いています。

もし内容に誤りがありましたら、 [IssueやPull Request](https://github.com/nineties/manifold-optimization)を頂けますとありがたいです。

1. [モチベーション](1-motivation)
2. [多様体の定義](2-manifold)
3. [多様体の位相構造](3-topology)
4. [可微分写像、部分多様体](4-submanifold)
5. [多様体の構成方法](5-construction)
6. [接ベクトル空間](6-tangent)
7. [微分](7-derivative)
8. [リーマン多様体、勾配](8-riemann)
9. [レトラクション](9-retractions)
10. [直線探索](10-linesearch)


参考にした文献

- [Optimization Algorithms on Matrix Manifolds](https://press.princeton.edu/absil)
- [トロント大Marco Gaultieri先生の講義ノート](http://www.math.toronto.edu/mgualt/courses/18-367/)
- [Lee. Introduction to Smooth Manifolds](https://www.springer.com/jp/book/9780387217529)

