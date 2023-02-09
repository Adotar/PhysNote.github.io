---
layout: post
read_time: true
show_date: true
title: "QFT in Condensed Matter Physics : Propagator and Path Integral"
date: 2023-02-08
img: posts/20210420/post8-rembrandt.jpg
tags: [凝聚态物理, QFT, propagator, path integral]
category: opinion
author: Adotar
mathjax: yes
description: "The method of path integral is one of the most important approaches in modern physics. Using the concept of propagator can help us understand the core idea of this method. Here I just want to take some notes while I'm learn the QFT in condensed matter physics."
---
## Propagator in 3 kinds of representations

The physical difinition of propagator is : propagator is the probability of one particle evolute from one state to another state within a period of time .

### 1. Real-space / time representation

The propagator can be difined in real-space / time representation as :

<p style="text-align:center">\(
G(x,t;x',t')=-i\langle x|U(t,t')|x'\rangle =-i\delta_{x,x'}=-i\sqrt{\frac{m}{2\pi i\Delta t}}e^{i\frac{m(x-x')^2}{2\Delta t}}\\\\
\Delta t=t-t'
\)</p>

with $U(t,t')=e^{-iH(t-t')}$ is the time evolution operator in real-space. The third equation is true only when we are considering free particle ( $H=\frac{p^2}{2m}$) in real-space representation.

### 2. Energy / frequency representation

We consider a particle in energy-space : 

<p style="text-align:center">\(
H|n\rangle=\epsilon_n|n\rangle
\)</p>

Then we can define the propagator in energy / time representation :

<p style="text-align:center">\(
G(n,t;n',t')=-i\bra{n}U(t,t')\ket{n'}=-ie^{-i\epsilon_n(t-t')}\delta_{n,n'}
\)</p>

Transfer from time-space to frequency-space ( fourier transformation ) :

<p style="text-align:center">\(
G(n,n';\omega)=\frac{1}{\omega-\epsilon_n+i0^+}\delta_{n,n'}
\)</p>

It's easily to find that there's a pole when $\omega=\epsilon_n-i0^+$ , and we use $0^+$ to converge the integral of fourier transformation. 

We need to emphasize that pole has to be considered when we transfer from frequency-space to time-space doing the inverse fourier transformation :

<p style="text-align:center">\(
G(n,n';\Delta t)=\frac{1}{2\pi}\int G(n,n';\omega)e^{-i\omega t}d\omega=\frac{1}{2\pi}\int \frac{\delta_{n,n'}}{\omega-\epsilon_n+i0^+}e^{-i\omega t}d\omega=-ie^{-i\epsilon_nt}
\)</p>

To solve this integral ( Cathy integral ) , we will use the residual concentration .

### 3. Path integral representation

#### 3.1 Path integral

I'm trying to provide a physical insight of the method of path integral . Considering an event that a particle traveling from $(x_a,t_a)$ to $(x_b,t_b)$ , the probability of which can be calculated according to the difinition of function $iG(x_b,t_b;x_a,t_a)$ . There are many paths that the particle can choose to travel along , we can imagine one of the paths going through the $(x,t)$ . It easily to calculate the probability as :

<p style="text-align:center">\(
P_{x_a\rightarrow x\rightarrow x_b}=P_{x_a\rightarrow x}\times P_{x\rightarrow x_b}
\)</p>

With the subscript means the path .

Meanwhile , there is not only one path the particle can choose . So , the real probability of it traveling from $(x_a,t_a)$ to $(x_b,t_b)$ need to consider all of the paths , which means we have to do an integral :

<p style="text-align:center">\(
iG(x_b,t_b;x_a,t_a)&=P_{x_a\rightarrow x_b}=\int P_{x_a\rightarrow x\rightarrow x_b}dx=\int P_{x_a\rightarrow x}\times P_{x\rightarrow x_b}dx\\\\
=\int iG(x_b,t_b;x,t)\cdot iG(x,t;x_a,t_a)dx
\)</p>

This is the core idea of the path integral .

#### 3.2 Propagator in path integral representation

There are 3 mean steps when we express the propagator in path integral representation :

(1) Devide the path into N slides ;

(2) Change the summation into integral (Using the limit of $N\rightarrow \infty$) ;

(3) Express the propagator in the form of action quantity

<p style="text-align:center">\(
iG(x_b,t_b;x_a,t_a)=\int iG(x_b,t_b;x_{N-1},t_{N-1})\cdot iG(x_{N-1},t_{N-1};x_{N-2},t_{N-2})\\\\
\cdots iG(x_1,t_1;x_a,t_a)dx_1dx_2\cdots dx_N\\\\
\xlongequal[x_a=x_0]{x_b=x_N} \int \prod_{j=1}^NiG(x_j,t_j;x_{j-1},t_{j-1})dx_1dx_2\cdots dx_N\ \cdots(1)\\\\
\xlongequal[H=\frac{p^2}{2m},N\rightarrow \infty]{Free\ Particle}(\frac{m}{2\pi i\Delta t})^{\frac{N}{2}}\int \prod_{j=1}^Ne^{i\frac{m}{2}(\frac{x_j-x_{j-1}}{\Delta t})^2\Delta t}dx_1dx_2\cdots dx_N\ \cdots(2)\\\\
=\sqrt{\frac{m}{2\pi i(t_b-t_a)}}e^{i\frac{m}{2N}\frac{(x_b-x_a)^2}{t_b-t_a}}\ \cdots(3)
\)</p>