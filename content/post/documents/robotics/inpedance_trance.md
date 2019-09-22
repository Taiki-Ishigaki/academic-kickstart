---
title: インピーダンス変換 
share: false  # Show social sharing links?
view: ["3"]
date: "2019-09-18"
markup: mmark
abstruct: ""
draft: true
---

タスク空間での剛性を関節空間での剛性に変換することを考える.タスクの自由度を$l$,関節の自由度を$m$として,冗長な関節自由度をもつ時を考える.($m>l$)この時,関節空間の剛性 $K_{\theta}$ は正則でなくなり,関節空間のコンプライアンス$C_{\theta}$が定まらない.
タスク空間の剛性$K$は正則であるとして,この時のタスク空間でのコンプライアンス $C$は

$$C=K^{-1}=J C_\theta J^T \tag{1}$$

上式を満たす,関節空間でのコンプライアンス$C_\theta$を求める.この方程式に関して以下の性質が成り立つ.  

## 1) 解の存在性  

「姿勢に特異点にない限り,関節空間のコンプライアンス$C_\theta$に関する方程式$(1)$は解をもつ」  

proof)
式$(1)$が解をもつための必要十分条件は

$$ JJ^{\sharp}C(JJ^{\sharp})^T = C \tag{2}$$

が成立することを示す.$J^{\sharp}$は擬似逆行列である.  
式$(1)$に解が存在すると、式$(2)$の左辺に$C$に式$(1)$を代入すると,

$$ JJ^{\sharp}(J C_\theta J^T)(JJ^{\sharp})^T = (JJ^{\sharp}J)C_{\theta}(JJ^{\sharp}J)^T = J C_\theta J^T = C \tag{3}$$

となり,式$(2)$が成立することがわかる.
式$(2)$が成立すると,式$(1)$と比較すると

$$ JJ^{\sharp}C(JJ^{\sharp})^T = C \\
J J^{\sharp}C(J^{\sharp})^TJ^T = J C_\theta J^T \\
 C_\theta = J^{\sharp}C(J^{\sharp})^T \tag{4}$$

がひとつの解となる.よって式$(2)$は式$(1)$が解をもつための必要十分条件である.
$m>l$で関節の自由度が冗長で姿勢に特異点がない時に, $J$は行に対してフルランクとなり, 擬似逆行列$J^{\sharp}$は

$$ J^{\sharp} = J^T(JJ^T)^{-1} \tag{5} $$

## 2) 一般解

「$(1)$式の方程式の一般解は
$$ C_\theta = J^{\sharp} C (J^{\sharp})^T + (Z - J^{\sharp}JZ(J^{\sharp}J)^T) \tag{6}$$
$Z \in \rm{R}^{m \times m}$は任意の行列である.」

proof)
式$(6)$の$C_\theta$を式$(1)$に代入すると,
$$ JC_\theta J^T = JJ^{\sharp}C(JJ^{\sharp})^T + J(Z - J^{\sharp}J Z (J^{\sharp}J)^T)J^T = C \tag{7}$$
となるため,式$(6)$の$C_\theta$は式$(1)$の解である.
また,$X$を任意の解とすると,
$$ Z = X - J^{\sharp}C(J^{\sharp})^T \tag{8}$$
として,
$$ X = J^{\sharp}C(J^T)^{\sharp} + (Z - J^{\sharp}J Z (J^{\sharp}J)^T) \tag{9}$$
と表すことができる.

## 3) 最小ノルム解

「式$(1)$の方程式の解のうち
$$ {C_\theta}^* = J^{\sharp} C (J^T)^\sharp$$
は最小ノルムを有する.ここでのマトリクスノルムは$\|C_\theta \| = \{tr({C_\theta}^T C_\theta)\}^{1/2}$を用いる.」
$tr(A)$は行列$A$の対角和.

## Reference

- T.Tsuji, et al. : 1988 冗長性を有する上肢多自由度運動におけるインピーダンス変換法
- T.Tsuji, et al. : 1990 冗長性を利用したマニピュレータの関節コンプライアンス調節
