---
layout: post
read_time: true
show_date: true
title: "QFT in Condensed Matter Physics (3)"
date: 2023-03-03
img: posts/20230303/levLandau.jpeg
tags: [凝聚态物理, QFT, path integral, fermion, coherent state, wick theorem, Grassmann variable]
category: opinion
author: Adotar
mathjax: yes
description: "Grassmann algebra and fermion coherent state are the gate we have to cross when we are entering the field of electron correlation system."
---
# Fermion Coherent State 

In this chapter, I divide it in three parts. The first part is meaning to talk about the math preparation before going into the fermion coherent state, the other part is about the path integral for the coherent state and the partition function of fermions. Last but not least, I gonna give a brief introduction and application of wick theorem.

## 1. Math Preparation

### 1.1 Fermion Coherent State

Fermion coherent state is the eigenstate of fermion annihilation operator:

<p style="text-align:center">\(
\hat{c}|\xi\rangle=\xi|\xi\rangle
\)</p>

### 1.2 Grassmann Variable

Why do we need the grassmann variable in fermion coherent state which we didn't use in boson's? The answer is clear, the creation and annihilation operators of fermions are anticommutative. So when we change the order of the fermion operators, there's always an extra minus sign which didn's show up in boson's.

Here are some properties of grassmann variable and grassmann algebra:

(1) Anticommutativity

<p style="text-align:center">\(
\{\xi_i,\xi_j\}=\{\bar{\xi_i},\bar{\xi_j}\}=\{\bar{\xi_i},\xi_j\}=\xi^2=0
\)</p>

<p style="text-align:center">\(
\{\xi_i,\hat{c}_j\}=\{\bar{\xi_i},\hat{c}_j\}=\{\xi_i,\hat{c}_j^{\dagger}\}=\{\bar{\xi_i},\hat{c}_j^{\dagger}\}=0
\)</p>

(2) Analytic properties

<p style="text-align:center">\(
\xi^2=0\Rightarrow \xi^n=0,n\geq 2
\)</p>

<p style="text-align:center">\(
\partial_{\xi}(\bar{\xi}\xi)=-\partial_{\xi}(\xi\bar{\xi})=-\bar{\xi}
\)</p>

Since then

<p style="text-align:center">\(
\psi(\xi,\bar{\xi})=\psi_0+\psi_1\xi+\psi_2\bar{\xi}+\psi_{12}\bar{\xi}\xi
\)</p>

<p style="text-align:center">\(
\partial_{\xi}\psi(\xi,\bar{\xi})=\psi_1-\psi_{12}\bar{\xi} \ ,\ \partial_{\bar{\xi}}\psi(\xi,\bar{\xi})=\psi_2+\psi_{12}\xi
\)</p>

(3) Integration

<p style="text-align:center">\(
\int d\xi=\partial_{\xi}
\)</p>

### 1.3 Overlap, Unity & Trace

To construst the coherent state path integral for fermions, we need overlaps, unity and trace in term of Grassmann variables.

(1) Overlaps for multifermions system

<p style="text-align:center">\(
\begin{aligned}
\langle\xi|\xi'\rangle
&=\langle0|(1-\hat{c}\bar{\xi})(1-\xi'\hat{c}^{\dagger})|0\rangle \\\\
&=\langle0|1-\xi'\hat{c}^{\dagger}-\hat{c}\bar{\xi}+\hat{c}\bar{\xi}\xi'\hat{c}^{\dagger}|0\rangle \\\\
&=\langle0|1+\hat{c}\hat{c}^{\dagger}\bar{\xi}\xi'|0\rangle \\\\
&=1+\bar{\xi}\xi' \\\\
&=e^{\sum_{\alpha}\bar{\xi}_{\alpha}\xi_{\alpha}}
\end{aligned}
\)</p>

(2) Unity

<p style="text-align:center">\(
\begin{aligned}
\int\prod_{\alpha}d\bar{\xi}_{\alpha}d\xi_{\alpha}e^{-\sum_{\alpha}\bar{\xi}_{\alpha}\xi_{\alpha}}|\xi\rangle\langle\xi|
&=\int\prod_{\alpha}d\bar{\xi}_{\alpha}d\xi_{\alpha}e^{-\sum_{\alpha}\bar{\xi}_{\alpha}\xi_{\alpha}}(1-\xi\hat{c})|0\rangle\langle0|(1-\hat{c}^{\dagger}\bar{\xi}) \\\\
&=\int\prod_{\alpha}d\bar{\xi}_{\alpha}d\xi_{\alpha}e^{-(\bar{\xi}\xi+\xi\hat{c}^{\dagger}-\bar{\xi}\hat{c})}|0\rangle\langle0| \\\\
&\xlongequal{\eta=\xi-\hat{c}}\int\prod_{\alpha}d\bar{\xi}_{\alpha}d\xi_{\alpha}e^{-\bar{\eta}\eta+\hat{c}^{\dagger}\hat{c}}|0\rangle\langle0| \\\\
&=\int\prod_{\alpha}d\bar{\xi}_{\alpha}d\xi_{\alpha}e^{-\bar{\eta}\eta}(1+\hat{c}^{\dagger}\hat{c})|0\rangle\langle0| \\\\
&\xlongequal{\partial_{\eta}=\partial_{\xi-\hat{c}}=\partial_{\xi}}\partial_{\bar{\eta}}\partial_{\eta}e^{-\bar{\eta}\eta} \\\\
&=1
\end{aligned}
\)</p>

(3) Trace

<p style="text-align:center">\(
Tr\hat{O}=\int\prod_{\alpha}d\bar{\xi}_{\alpha}d\xi_{\alpha}e^{-\sum_{\alpha}\bar{\xi}_{\alpha}\xi_{\alpha}}\langle-\xi|\hat{O}|\xi\rangle
\)</p>

## 2. Path Integration

### 2.1 Fermion Coherent State

For Hubbard model, we have:

<p style="text-align:center">\(
\hat{H}=-t\sum_{i,j,\sigma}\hat{c}_{i\sigma}^{\dagger}\hat{c}_{j\sigma}+U\sum_in_{i\uparrow}n_{i\downarrow}
\)</p>

And do the path integration:

<p style="text-align:center">\(
\begin{aligned}
&\langle\psi_f,t_f|\hat{U}(t_f,t_i)|\psi_i,t_i\rangle=\langle\psi_f|e^{-\frac{i}{\hbar}\hat{H}(t_f-t_i)}|\psi_i\rangle \\\\
&=\lim_{M\rightarrow\infty}\int\prod_{k=1}^{M-1}\prod_{\alpha}d\bar{\xi}_{\alpha k}d\xi_{\alpha k}\exp[-\sum_{\alpha}\bar{\xi}_{\alpha k}\dot{\xi}_{\alpha k}\Delta t-\frac{i}{\hbar}\Delta t\hat{H}(\bar{\xi}_k,\xi_{k-1})] \\\\
&=\int D[\bar{\xi},\xi]e^{\frac{i}{\hbar}S(\bar{\xi},\xi)}
\end{aligned}
\)</p>

with

<p style="text-align:center">\(
S(\bar{\xi},\xi)=\int_{t_i}^{t_f}dt[i\hbar\bar{\xi}\dot{\xi}-H(\bar{\xi,\xi})]
\)</p>

<p style="text-align:center">\(
\int D[\bar{\xi},\xi]=\lim_{M\rightarrow\infty}\int\prod_{k=1}^{M-1}\prod_{\alpha}d\bar{\xi}_{\alpha k}d\xi_{\alpha k}
\)</p>

### 2.2 Partition Function

Using the result in chapter 1.3.(3), the partition function can be written as:

<p style="text-align:center">\(
\begin{aligned}
Z&=Tr\ e^{-\beta(\hat{H}-\mu\hat{N})} \\\\
&=\int\prod_{\alpha}d\bar{\xi}_{\alpha}d\xi_{\alpha}e^{-\sum_{\alpha}\bar{\xi}_{\alpha}\xi_{\alpha}}\langle-\xi|e^{-\beta(\hat{H}-\mu\hat{N})}|\xi\rangle \\\\
&=\int D[\bar{\xi},\xi]e^{-S(\bar{\xi},\xi)}
\end{aligned}
\)</p>

with

<p style="text-align:center">\(
S(\bar{\xi},\xi)=\int_0^{\beta}d\tau\sum_{\alpha}\bar{\xi}_{\alpha}(\tau)(\frac{\partial}{\partial\tau}-\mu)\xi_{\alpha}(\tau)+\hat{H}(\bar{\xi}(\tau),\xi(\tau))
\)</p>

<p style="text-align:center">\(
\int D[\bar{\xi},\xi]=\lim_{M\rightarrow\infty}\int\prod_{k=1}^{M-1}\prod_{\alpha}d\bar{\xi}_{\alpha k}d\xi_{\alpha k}
\)</p>

## 3. Wick Theorem

Wick theorem is a method to reduce the complexity when we are solving a combinatorics problem. It is generally used in quantum field theory when we are drawing the Feynman diagram.

The theorem says that all of the time ordered product can be expanded by the normal ordered product. It can be written as:

<p style="text-align:center">\(
\begin{aligned}
T\prod_{i=1}^m\hat{A}_i&=:T\prod_{i=1}^m\hat{A}_i:+\sum_{\alpha,\beta}\overline{\hat{A}_{\alpha}\hat{A}_{\beta}}:T\prod_{i\neq\alpha,\beta}\hat{A}_i: \\\\
&+\sum_{\alpha,\beta;\gamma,\delta}\overline{\hat{A}_{\alpha}\hat{A}_{\beta}}\ \overline{\hat{A}_{\gamma}\hat{A}_{\delta}}:T\sum_{\alpha,\beta;\gamma,\delta}\hat{A}_i:+\cdots
\end{aligned}
\)</p>

with $T$ is the time ordering operator, which can arrange the operators in chronological order (each time the order of the creation or annihilation operators of fermion are changed, put a minus in the front). And $:ABC:$ is the normal order of operators, which arrange the operators in the order that all creation operators precede and annihilation operators come after (remember the minus). And $\overline{ABC}$ is the contraction over $T(ABC)$:

<p style="text-align:center">\(
\overline{ABC}=T(ABC)-:ABC:
\)</p>


