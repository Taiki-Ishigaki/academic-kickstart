---
title: 行列の指数・対数
share: false  # Show social sharing links?
view: ["3"]
date: "2020-01-08"
markup: mmark
abstruct: ""
draft: false
categories : ["math"]
tags : []
---
## 対角化可能行列の指数関数
ある正方行列$A (= P \Lambda P^{-1} )$が対角可能なとき

$$
A^k = (P \Lambda P^{-1})^k = (P \Lambda P^{-1}) \cdots (P \Lambda P^{-1}) = P \Lambda^k P
$$

となる。ただし、$ \Lambda = \rm{diag}(\lambda_i)$

このとき

$$
e^{Ax} = e^{(P \Lambda P^{-1})x} = E + (P \Lambda P^{-1}) x + \frac{(P \Lambda P^{-1})^2 x^2}{2!} + \cdots + \frac{(P \Lambda P^{-1})^k x^k}{k!} + \cdots \\
= P (E + \Lambda x + \frac{ \Lambda^2 x^2}{2!} + \cdots + \frac{\Lambda^k x^k}{k!} + \cdots) P^{-1} = P e^{\Lambda} P^{-1}
$$
