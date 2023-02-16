---
layout: post
read_time: true
show_date: true
title: "QFT in Condensed Matter Physics (2)"
date: 2023-02-16
img: posts/20230216/Feynman.jpg
tags: [凝聚态物理, QFT, propagator, path integral, boson, coherent state]
category: opinion
author: Adotar
mathjax: yes
description: "Boson coherent state can be used to discribe a special state of bosons, which won't be change under the action of annihilation operator. This article meaning to give a brief introduction of boson coherent state, and give the main calculation result and ideas. "
---
# Boson Coherent State 

This article meaning to give a brief introduction of boson coherent state, and give the main calculation result and ideas. 

## 1. Definition

Boson coherent state is the eigenstate of boson annihilation operator:

<p style="text-align:center">\(
\hat{a}|\alpha \rangle=\alpha|\alpha \rangle
\)</p>

Utilizing:

<p style="text-align:center">\(
\langle \alpha|\alpha \rangle=1
\)</p>

we can get:

<p style="text-align:center">\(
|\alpha \rangle=e^{-\frac{|\alpha|^2}{2}}\sum_{n=0}^{\infty}\frac{\alpha^n}{\sqrt{n!}}|n \rangle
\)</p>

## 2. Overlap, Overcompleteness

Utilizing the definition of boson coherent state, it is easy to compute the overlap between two states in the space of coherent state:

<p style="text-align:center">\(
\begin{aligned}
\langle \alpha|\beta \rangle
&=e^{-\frac{|\alpha|^2}{2}}\sum_{m=0}^{\infty}\frac{\alpha^m}{\sqrt{m!}}\langle m|\cdot e^{-\frac{|\beta|^2}{2}}\sum_{n=0}^{\infty}\frac{\beta^n}{\sqrt{n!}}|n \rangle \\\\
&=e^{-\frac{|\alpha|^2+|\beta |^2}{2}+\alpha^*\beta }
\end{aligned}
\)</p>

To prove the overcompleteness of this space of state, we ansatz a normalized function:

<p style="text-align:center">\(
\int f(\alpha)|\alpha \rangle \langle \alpha|d\alpha=1
\)</p>

Utilizing:

<p style="text-align:center">\(
\langle n|1|m\rangle =\delta_{mn}=\int f(\alpha)\langle n|\alpha\rangle\langle\alpha|m\rangle d\alpha
\)</p>

and we asumme that

<p style="text-align:center">\(
f(\alpha)=f(|\alpha|)=f(|r\cos{\psi}+ir\sin{\psi}|)=f(r)=a
\)</p>

so:

<p style="text-align:center">\(
\begin{aligned}
\langle n|1|m\rangle
&=\int f(\alpha) \langle n|e^{-\frac{|\alpha|^2}{2}}\sum_{n'=0}^{\infty}\frac{\alpha^{n'}}{\sqrt{n'!}}|n' \rangle\cdot e^{-\frac{|\alpha|^2}{2}}\sum_{m'=0}^{\infty}\frac{\alpha^{m'}}{\sqrt{m'!}}|m' \rangle d\alpha \\\\
&=2a\delta_{mn}\int_0^{\infty}\frac{e^{-r^2}r^{2n+1}}{n!}dr \\\\
&=\pi a\delta_{mn} \\\\
&=\delta_{mn} \\\\
&\Rightarrow a=\frac{1}{\pi} \\\\
&\Rightarrow 1=\frac{1}{\pi}\int |\alpha\rangle\langle\alpha|d\alpha
\end{aligned}
\)</p>

So we can consider that the space stretched out by boson coherent state is overcomplete.

## 3. Path Integral

According to the conclusion of [the last note about path integral](https://adotar.github.io/PhysNote.github.io/QFT-propagator&path-integral.html) and the overcompleteness of boson coherent state, it's easy to compute the propagator of bosons:

<p style="text-align:center">\(
iG(\alpha_b,t_b;\alpha_a,t_a)=\frac{1}{\pi^{N-1}}\int\prod_{j=1}^NiG(\alpha_j,t_j;\alpha_{j-1},t_{j-1})d\alpha_1d\alpha_2\cdots d\alpha_{N-1}
\)</p>

With

<p style="text-align:center">\(
\begin{aligned}
iG(\alpha_j,t_j;\alpha_{j-1},t_{j-1})&=\langle \alpha_j|\hat{U}(t_j,t_{j-1})|\alpha_{j-1}\rangle \\\\
&=\langle\alpha_j|e^{-i\hat{H}\Delta t}|\alpha_{j-1}\rangle,\ \Delta t=t_j-t_{j-1}=\frac{t_b-t_a}{N}\rightarrow0 \\\\
&=[1-i\hbar\omega\Delta t(\alpha_j^*\alpha_{j-1}+\frac{1}{2})]\langle\alpha_j|\alpha_{j-1}\rangle \cdots (1) \\\\
&=e^{i\Delta t[-\frac{i}{2\Delta t}(-\alpha_j\alpha_j^*-\alpha_{j-1}\alpha_{j-1}^*+2\alpha_j^*\alpha_{j-1})-\hbar\omega\alpha_j^*\alpha_{j-1}]}e^{-\frac{i\hbar\omega\Delta t}{2}} \\\\
&=Ae^{i\Delta tL}
\end{aligned}
\)</p>

To get the expression (1), we should use the Taylor expansion:

<p style="text-align:center">\(
\lim_{x\rightarrow0}e^x=\lim_{x\rightarrow0}\sum_{n=0}^{\infty}\frac{x^n}{n!}\approx1+x
\)</p>

In the expression of the propagator, the variable $L$ and the parameter $A$:

<p style="text-align:center">\(
\begin{aligned}
L&=-\frac{i}{2\Delta t}(-\alpha_j\alpha_j^*-\alpha_{j-1}\alpha_{j-1}^*+2\alpha_j^*\alpha_{j-1})-\hbar\omega\alpha_j^*\alpha_{j-1} \\\\
&=\frac{i}{2}[\alpha^*(t)\dot{\alpha}(t)-\dot{\alpha}^*(t)\alpha(t)]-\hbar\omega\alpha^*(t)\alpha(t)\ ;
\end{aligned}
\)</p>

And

<p style="text-align:center">\(
A=e^{-\frac{i\hbar\omega\Delta t}{2}}
\)</p>

Eventually, we can write the propagator of boson coherent state as an expression like this:

<p style="text-align:center">\(
iG(\alpha_b,t_b;\alpha_a,t_a)=(\frac{A}{\pi})^{N-1}\int e^{\int_{t_a}^{t_b}L(\alpha,\alpha^*,t)dt}d\alpha_1d\alpha_2\cdots d\alpha_{N-1}
\)</p>

Here the conclusion of the propagator helps us to understand how the coherent state of bosons evolute from one state to another state.