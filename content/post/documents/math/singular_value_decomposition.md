---
title: 特異値分解
share: false  # Show social sharing links?
view: ["3"]
date: "2019-10-17"
markup: mmark
abstruct: ""
draft: false
categories : ["math"]
tags : []
---

実数行列:$A \in \mathbb{R}^{m \times n}$の特異値分解が以下のように与えられる．

$$
A = USV^T =  
\left[
\begin{array}{rr}
U_1 & U_2
\end{array}
\right]
\left[
\begin{array}{rr}
\Sigma_{r \times r} & O_{r \times (n-r)} \\
O_{(m-r) \times r} & O_{(m-r) \times (n-r)}
\end{array}
\right]
\left[
\begin{array}{rr}
{V_1}^T \\
{V_2}^T
\end{array}
\right]
$$

$$
\Sigma = \rm{diag}(\sigma_1, ... \sigma_r)
$$

ここでrank$(A) = r$、$U \in \mathbb{R}^{m \times m}$，$V \in \mathbb{R}^{n \times n}$は直交行列，$\sigma_i (i = 1, ... r)$は$A$の特異値  

擬似逆行列は

$$
A^{\sharp} =  
\left[
\begin{array}{rr}
U_1 & U_2
\end{array}
\right]
\left[
\begin{array}{rr}
\Sigma_{r \times r}^{-1} & O_{r \times (n-r)} \\
O_{(m-r) \times r} & O_{(m-r) \times (n-r)}
\end{array}
\right]
\left[
\begin{array}{rr}
{V_1}^T \\
{V_2}^T
\end{array}
\right]
$$

$U$，$V$は直交行列なので

$$
U^T U = U U^T = E_m , V^T V = V V^T = E_n
$$

そこで

$$
V^T V =
\left[
\begin{array}{rr}
V_1^T \\
V_2^T
\end{array}
\right]
\left[
\begin{array}{rr}
V_1 & V_2
\end{array}
\right] =  
\left[
\begin{array}{rr}
V_1^T V_1 & V_1^T V_2 \\
V_2^T V_1 & V_2^T V_2
\end{array}
\right] =  
E_n
$$

$$
V V^T =
\left[
\begin{array}{rr}
V_1 & V_2
\end{array}
\right]
\left[
\begin{array}{rr}
V_1^T \\
V_2^T
\end{array}
\right] =  
V_1 V_1^T + V_2 V_2^T = E_n
$$

であるので

$$
V_1^T V_1 = E_r, V_2^T V_2 = E_{(n - r)}, V_1^T V_2 = V_2^T V_1 = O
$$

ここで$V_1$，$V_2$は必ずしも正方行列ではなく$V_1 V_1^T$，$V_2 V_2^T$が単位行列ではない($A$が列フルランクなら$V = V_1$で正方行列)
