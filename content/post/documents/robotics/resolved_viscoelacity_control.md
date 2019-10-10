---
title: 粘弾性分解制御
share: false  # Show social sharing links?
view: ["3"]
date: "2019-10-03"
markup: mmark
abstruct: ""
draft: true
categories : ["robotics"]
tags : []
---
## 前提

タスク空間の座標 $\boldsymbol{x} \in \mathbb{R}^{m \times m}$, 関節空間の座標 $\boldsymbol{\theta} \in \mathbb{R}^{n \times n}$で$m < n$の冗長自由度が存在する。

タスク空間のスティフネスを$K \in R$、コンプライアンスを$C (= K^{-1})$としタスク空間のスティフネスを$K_{\theta}$、コンプライアンスを$C_{\theta} (= {K_{\theta}}^{-1})$とする。

## 数式の準備

### 微分運動学

$$ \boldsymbol{J = \frac{\partial x}{\partial \theta} } \tag{1} $$

$$ \boldsymbol{\dot{x} = J \dot{\theta} } \tag{2} $$

$\delta \boldsymbol{\theta} << 1$で微小なとき以下が成り立つ

$$ \delta \boldsymbol{x} = \boldsymbol{J} \delta \boldsymbol{\theta} \tag{3} $$

仮想仕事の原理から

$$ {\delta \boldsymbol{x}}^T \boldsymbol{f} = {\delta \boldsymbol{\theta}}^T \boldsymbol{\tau} \tag{4}$$

$$ (\boldsymbol{J} \delta \boldsymbol{\theta})^T \boldsymbol{f} = {\delta \boldsymbol{\theta}}^T \boldsymbol{\tau} $$

$$  {\delta \boldsymbol{\theta}}^T \boldsymbol{J^T} \boldsymbol{f} = {\delta \boldsymbol{\theta}}^T \boldsymbol{\tau} $$

以上より

$$ \boldsymbol{J^T} \boldsymbol{f} = \boldsymbol{\tau} \tag{5} $$

### ヤコビ行列の擬似逆行列

ヤコビ行列 $ \boldsymbol{J} \in \mathbb{R}^{m \times n} (m < n)$なので

$$ \boldsymbol{J^{\sharp} = J^T(J J^T)^{-1}}$$

### 力と粘弾性

#### スティフネス

$$ \boldsymbol{f} = \boldsymbol{K} \delta \boldsymbol{x} \tag{6}$$

$$ \boldsymbol{\tau} = \boldsymbol{K_{\theta}} \delta \boldsymbol{\theta} \tag{7}$$

#### コンプライアンス

$$ \boldsymbol{C f} = \boldsymbol{K^{-1} f} =  \delta \boldsymbol{x} \tag{8}$$

$$ \boldsymbol{C_{\theta} \tau} = \boldsymbol{K_{\theta}^{-1} \tau} =  \delta \boldsymbol{\theta} \tag{9}$$

## 粘弾性の変換

### スティフネスの変換

(5)式に(6),(7)式を代入して

$$ \boldsymbol{J^T K} \delta \boldsymbol{x} = \boldsymbol{K_\theta} \delta \boldsymbol{\theta}$$

(3)式より

$$ \boldsymbol{J^T K J } \delta \boldsymbol{\theta} = \boldsymbol{K_\theta} \delta \boldsymbol{\theta}$$

$$ \boldsymbol{J^T K J } = \boldsymbol{K_\theta} \tag{10}$$

冗長自由度をもつ時、$\boldsymbol{K_{\theta}}$は正則ではなくなる

### コンプライアンスの変換

(3)式に(8),(9)式を代入して

$$ \boldsymbol{C f} =  \boldsymbol{J C_{\theta} \tau} $$

(5)式より

$$ \boldsymbol{C f} =  \boldsymbol{J C_{\theta} J^T f} $$

$$ \boldsymbol{C} =  \boldsymbol{J C_{\theta} J^T }　\tag{11} $$

#### コンプライアンスの一般解

(11)式から$\boldsymbol{C_{\theta}}$の一般解は、目標値を$\boldsymbol{Y^{-1}}$として、以下の最小化問題を解くことで求めることができる。

$$ \rm{min} \  \frac{1}{2} \parallel \boldsymbol{Y^{-1} - C_{\theta}} \parallel ^2 \\  
\rm{subject\ to} \  \boldsymbol{C = J C_{\theta} J^T } \tag{12}$$

この時の解は以下で示される。

$$ \boldsymbol{C_{\theta} = J^{\sharp} C {J^{T}}^{\sharp} + (Y^{-1} - J^{\sharp}J Y^{-1} J^T {J^{T}}^{\sharp})}  \tag{13}$$

## 粘弾性の変換(動力学考慮)

### 準備

#### Inertia-weighted pseudo inverse

運動エネルギーを最小化する一般化逆行列

$$ \boldsymbol{ {J^T}^{\dagger} = (J M^{-1} J^T)^{-1}J M^{-1} }  \tag{14}$$

$$ \boldsymbol{f = {J^T}^{\dagger}} \boldsymbol{\tau} \tag{15}$$

この時$\tau$の一般解は以下の最小化問題(17)式を解いて(18)式になる

$$ \rm{min} \  \frac{1}{2} \parallel \boldsymbol{y - \tau} \parallel ^2 \\  
\rm{subject\ to} \  \boldsymbol{f = {J^T}^{\dagger}} \boldsymbol{\tau} \tag{17}$$

$$ \boldsymbol{\tau = J^T f + (E - J^T{J^{\dagger}}^T)y} \tag{18}$$

### スティフネスの変換(動力学)

(15)式に(6),(7)式を代入して

$$ \boldsymbol{K} \delta \boldsymbol{x} = \boldsymbol{ {J^T}^{\dagger} } \boldsymbol{K_{\theta}} \delta \boldsymbol{\theta} $$

(3)式より
$$ \boldsymbol{K} \boldsymbol{J} \delta \boldsymbol{\theta} =  \boldsymbol{ {J^T}^{\dagger}} \boldsymbol{K_{\theta}} \delta \boldsymbol{\theta}$$

$$ \boldsymbol{K} \boldsymbol{J} =  \boldsymbol{ {J^T}^{\dagger}} \boldsymbol{K_{\theta}} \tag{19}$$

#### スティフネスの一般解(動力学)

$$ \rm{min} \  \frac{1}{2} \parallel \boldsymbol{Y - K_{\theta}} \parallel ^2 \\
\rm{subject\ to} \  \boldsymbol{K} \boldsymbol{J} =  \boldsymbol{ {J^T}^{\dagger}} \boldsymbol{K_{\theta}} \tag{20}$$

$$ \boldsymbol{K_{\theta} = J^T K J + (E - J^T{J^T}^{\dagger})Y} \tag{21}$$

(21)式は(18)式を$\boldsymbol{y = Y}\delta\boldsymbol{\theta}$として、(6)、(7)式を代入しても求まる。

### コンプライアンスの変換(動力学)

(3)式に(8),(9)式を代入して

$$ \boldsymbol{Cf = J C_{\theta} \tau} $$

(15)式より

$$ \boldsymbol{C {J^T}^{\dagger} \tau = J C_{\theta} \tau} $$

$$ \boldsymbol{C {J^T}^{\dagger} = J C_{\theta}} \tag{22}$$

#### コンプライアンスの一般解(動力学)

$$ \rm{min} \  \frac{1}{2} \parallel \boldsymbol{Y^{-1} - C_{\theta}} \parallel ^2 \\
\rm{subject\ to} \  \boldsymbol{C {J^T}^{\dagger} = JC_{\theta}} \tag{23}$$

$$ \boldsymbol{C_{\theta} = J^{\sharp}C{J^T}^{\dagger} + (E - J^{\sharp}J) Y^{-1}} \tag{24} $$

## 付録

$$ 
\rm{min} \  \frac{1}{2} \parallel \boldsymbol{Y^{-1} - C_{\theta}} \parallel ^2 \\
\rm{subject\ to} \  \boldsymbol{C {J^T}^{\dagger} = JC_{\theta}} 
$$

をラグランジュの未定乗数法を用いて解く．$\lambda$をラグランジュの未定乗数として，ラグランジアンを$L$として

$$
L = \rm{min} \  \frac{1}{2} \parallel \boldsymbol{Y^{-1} - C_{\theta}} \parallel ^2 + {\lambda}^T (JC_{\theta} - C{J^T}^{\dagger})
$$

$$
\frac{\partial L}{\partial C_{\theta}} = - (Y^{-1} - C_{\theta}) + J^T \lambda  = 0 \tag{25}
$$

$$
\frac{\partial L}{\partial \lambda} = JC_{\theta} - C{J^T}^{\dagger} = 0 \tag{26}
$$

(25)，(26)から$C_{\theta}$を消去して

$$
J (Y^{-1} - J^T \lambda) - C {J^T}^{\dagger} = 0 \\
J J^T \lambda = J Y^{-1} - C {J^T}^{\dagger} \\
\lambda = (J J^T)^{-1} (J Y^{-1} - C {J^T}^{\dagger}) \\
$$

$$
\lambda = {J^T}^{\sharp} Y^{-1} -  (J J^T)^{-1} C {J^T}^{\dagger} \tag{27}
$$

(25)，(27)から$\lambda$を消去して$C_{\theta}$を求める

$$
\begin{align}
C_{\theta} &= Y^{-1} - J^T \lambda \\
&= Y^{-1} - J^T {J^T}^{\sharp} Y^{-1} - J^T (J J^T)^{-1} C {J^T}^{\dagger} \\
&= J^{\sharp} C {J^T}^{\dagger} + (E - J^T {J^T}^{\sharp}) Y^{-1}
\end{align}
$$

以上より$C_{\theta}$が求まる

$$ C_{\theta} = J^{\sharp}C{J^T}^{\dagger} + (E - J^{\sharp}J^T) Y^{-1}$$

## メモ

### 動力学レベルのスティフネスとコンプライアンスの比較

(21)式、(24)式から求まる$\boldsymbol{K_{\theta} , C_{\theta} (= {K_{\theta}^{-1}}) }$が一致するのは任意の行列Yを以下のようにスカラー倍にした時

$$ \boldsymbol{Y = kE}$$

### 動力学と運動学のつながり

$$ \boldsymbol{C {J^T}^{\dagger} \tau = J C_{\theta} \tau} $$

に(5)式を代入すると
$$ \boldsymbol{C {J^T}^{\dagger} J^T f = J C_{\theta} J^T f} $$

$\boldsymbol{ {J^T }^{\dagger} J^T = E}$なので

$$ \boldsymbol{C  f = J C_{\theta} J^T f} $$

以下のように(11)式が求まる

$$ \boldsymbol{C = J C_{\theta} J^T } $$

よって(22)式と(11)式を同時に満たす,$\boldsymbol{C, C_{\theta}}$が存在し、そこで(22)式に(11)式を代入すると

$$ \boldsymbol{J C_{\theta} J^T {J^T}^{\dagger} = J C_{\theta}} $$

この時$J^T {J^T}^{\dagger} \neq E$なので一見、両辺は等しくないように見える

これは上の式変換に(18)式ではなく(5)式を用いることで$C_{\theta}$が以下を満たすように限定されるはず

$$\boldsymbol{C_{\theta} J^T {J^T}^{\dagger} = C_{\theta}}$$

---

ちなみに以下の式は導くことができた

$$\boldsymbol{ J^T {J^T }^{\dagger}K_{\theta} = K_{\theta}}$$

proof)

$$ \boldsymbol{\tau =J^T f}\tag{A.1}$$

$$ \boldsymbol{f = {J^T}^{\dagger} \tau} \tag{A.2}$$

(A.1)と(A.2)を用いて$\boldsymbol{f}$を消去すると

$$ \boldsymbol{\tau = J^T {J^T}^{\dagger}  \tau}$$

$$(中略)$$

$$ \boldsymbol{K_{\theta} = J^T {J^T}^{\dagger} K_{\theta}}$$

---

$$\boldsymbol{ {C_{\theta}}^T J^T {J^T}^{\dagger}  = {C_{\theta}^T}}$$

proof)
$$ \boldsymbol{f = {J^T}^{\dagger} \tau} \tag{B.1}$$

仮想仕事の原理より

$$ {\delta \boldsymbol{x}}^T \boldsymbol{f} = {\delta \boldsymbol{\theta}}^T \boldsymbol{\tau}$$

$$ {\delta \boldsymbol{x}}^T \boldsymbol{ {J^T}^{\dagger} \tau} = {\delta \boldsymbol{\theta}}^T \boldsymbol{\tau} $$

$$ \boldsymbol{J^{\dagger}} {\delta \boldsymbol{x}}  = {\delta \boldsymbol{\theta}} \tag{B.2}$$

微分運動学より

$$ \delta \boldsymbol{x} = \boldsymbol{J} \delta \boldsymbol{\theta} \tag{B.3} $$

(B.2)に(B.3)を代入すると

$$ \boldsymbol{J^{\dagger}} \boldsymbol{J} \delta \boldsymbol{\theta}  = {\delta \boldsymbol{\theta}} $$

$$ (中略) $$

$$ \boldsymbol{J^{\dagger}} \boldsymbol{J} \boldsymbol{C_{\theta}}  = \boldsymbol{C_{\theta}} $$

転置して

$$\boldsymbol{ {C_{\theta}}^T J^T {J^T}^{\dagger}  = {C_{\theta}^T}} \tag{B.4}$$

---
