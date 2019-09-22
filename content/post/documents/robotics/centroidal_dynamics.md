---
title: 重心動力学
share: false  # Show social sharing links?
view: ["3"]
date: "2019-09-22"
markup: mmark
abstruct: ""
draft: false
categories : ["robotics"]
tags : []
---
## 剛体の運動方程式

$$
m_i \ddot{p_{G_i}} = \hat{f_i} + \sum_j f_{i, j} - m_i g \tag{1}
$$

$$
\dot{L_i} = \hat{\tau_i} + \sum_j \tau_{i, j} \tag{2}
$$

- $m_i$ : 剛体の質量  
- $p_{G_i}$ : 剛体の重心位置  
- $L_i$ : 剛体の重心まわりの角運動量  
- $\hat{f_i}$ : 剛体に働く外力
- $\hat{\tau_i}$ : 剛体に働く重心まわりのモーメント
- $f_{i, j}$ : 剛体間に働く力
- $\tau_{i, j}$ : 剛体間に働くモーメント

## 多体系の重心の運動方程式

剛体$l_i$($i = 1, ... n$)からなる多体系の重心に関する運動方程式を導出する.

まず, 重心$ p_G $を定義する.

$$
p_G = \frac{1}{m} \sum_i m_i p_{G_i} \tag{3}
$$

ここで$m$は剛体の全質量である.

重心の運動量は

$$
H_G = m \dot{p_G} \tag{4}
$$

重心に関する運動方程式は運動量の時間変化から(1),(4)式より以下のように求まる

$$
\dot{H_G} = m \ddot{p_G} = \sum_i m_i \ddot{p_{G_i}}
= \sum_i (\hat{f_i} + \sum_j f_{i,j} - m_i g)
= \sum_i \hat{f_i}  - m g
$$

$$
m \ddot{p_G} = \sum_i \hat{f_i}  - m g \tag{5}
$$

## 多体系の重心周りの角運動量に関する運動方程式

多体系の重心周りの角運動量に関する運動方程式を導出する.

重心周りの角運動量は

$$
L_G = \sum_i (L_i + (p_{G_i} - p_G) \times m_i \dot{p_i}) \tag{6}
$$

重心周りの角運動量に関する運動方程式は角運動量の時間変化から(2), (6)式より以下のように求まる

$$
\dot{L_G} = \sum_i (\dot{L_i} + (\dot{p_{G_i}} - \dot{p_G}) \times m_i \dot{p_i} + (p_{G_i} - p_G) \times m_i \ddot{p_i}) = \sum_i(\hat{\tau_i} + (p_{G_i} - p_G) \times \hat{f_i})
$$

$$
\dot{L_G} = \sum_i(\hat{\tau_i} + (p_{G_i} - p_G) \times \hat{f_i}) \tag{7}
$$

## 接触レンチ(contact wrench)

並進力成分とモーメント成分を合わせた6次元ベクトル

$$
\left[
\begin{array}{rr}
f_c \\
\tau_c \\
\end{array}
\right] =
\left[
\begin{array}{rr}
\sum_i \hat{f_i} \\
\sum_i(\hat{\tau_i} + p_{G_i} \times \hat{f_i}\\
\end{array}
\right]
$$

## 重心の運動方程式

$$
\begin{cases}
m \ddot{p_G} = f_c - mg \\
\dot{L} = \tau_c - p_G \times f_c
\end{cases}
$$

## Appendix

### 作用・反作用の法則

$$
f_{i, j} = - f_{j, i}
$$

$$
\tau_{i, j} + p_i \times f_{i, j} = - (\tau_{j, i} + p_j \times f_{j_i})
$$
