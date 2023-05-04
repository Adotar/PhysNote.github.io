---
layout: post
read_time: true
show_date: true
title: "Mean Field Approximation in Extended Hubbard Model"
date: 2023-05-04
img: posts/20230303/levLandau.jpeg
tags: [凝聚态物理, Mean Field Approximation, Extended Hubbard Model]
category: opinion
author: Adotar
mathjax: yes
description: "A note about my first research program"
---
# 1. Mean Field Approximation

## 1.1. Nearly Free Electron Approximation

In almost all of the text book about solid physics , there is always one section about the nearly free electron approximation . It is the first time when the students of physics getting to learn about one of the method of perturbation , which seems to create a mean field . It just has done one thing to the potential field in cristal , which is changing $V(x)$ into $\bar{V}+\Delta V$ , where $\Delta V=V(x)-\bar{V}$ , $\bar{V}$ is the **'mean field'** . Using the perturbation theory in quantum mechanics , we can easily do an approximate interpretation about the energy band structure in cristal . **[For further details .](https://solidstate.quantumtinkerer.tudelft.nl/11_nearly_free_electron_model/)**

## 1.2 Hartree Fock Approximation

The mean field approximation in this article is not what we talked about in section **1.1** . The mean field approximation we want to talk about is a non-perturbation method , and the main idea is **decoupling and recombination** . 

Using the anticommutation relation of fermion operators , we can **decouple** the multiplicity of fermions into a form of quadric . Using the physical insight of a physicist , you can guess which form is reasonable in the problem you care , and then do some acceptation or rejection , keep what you think is reasonable , which is **recombination **.

For example:

<p style="text-align:center">\(
\hat H_V=\frac{V}{2}\sum_{ij}\hat c_{i}^{\dagger}\hat c_{j}^{\dagger}\hat c_{j}\hat c_{i} \\
\)</p>

We can decouple it in **Hartree** mean field :

<p style="text-align:center">\(
\begin{aligned}
\hat H_V&=\frac{V}{2}\sum_{ij}\hat c_i^{\dagger}\hat c_i\hat c_j^{\dagger}\hat c_j \\
&=\frac{V}{2}\sum_{ij}\hat n_i\hat n_j \\
&=\frac{V}{2}\sum_{ij}(\langle\hat n_i\rangle+\delta\hat n_i)(\langle\hat n_j\rangle+\delta\hat n_j) \\
&=\frac{V}{2}\sum_{ij}\langle\hat n_i\rangle\langle\hat n_j\rangle+\langle\hat n_i\rangle\delta\hat n_j+\langle\hat n_j\rangle\delta\hat n_i+\delta\hat n_i\delta\hat n_j \\
&\approx\frac{V}{2}\sum_{ij}\langle\hat n_i\rangle\langle\hat n_j\rangle+\langle\hat n_i\rangle(\hat n_j-\langle\hat n_j\rangle)+\langle\hat n_j\rangle(\hat n_i-\langle\hat n_i\rangle) \\
&\approx\frac{V}{2}\sum_{ij}\langle\hat n_i\rangle\hat n_j+\langle\hat n_j\rangle\hat n_i-\langle\hat n_i\rangle\langle\hat n_j\rangle \\
&\equiv\hat V_H
\end{aligned}
\)</p>

also in **Fock** mean field :

<p style="text-align:center">\(
\begin{aligned}
\hat H_V&=\frac{V}{2}\sum_{ij}\hat c_i^{\dagger}(1-\hat c_j\hat c_j^{\dagger})\hat c_i \\
&=\frac{V}{2}\sum_{ij}\hat n_i-\frac{V}{2}\sum_{ij}\hat c_i^{\dagger}\hat c_j\hat c_j^{\dagger}\hat c_i \\
&\xlongequal[ignore\ it]{\frac{V}{2}\sum_{ij}\hat n_i=const}-\frac{V}{2}\sum_{ij}\hat c_i^{\dagger}\hat c_j\hat c_j^{\dagger}\hat c_i \\
&\cdots \\
&\approx-\frac{V}{2}\sum_{ij}\langle\hat b_{ij}\rangle\hat b_{ij}+\langle\hat b_{ji}\rangle\hat b_{ji}-\langle\hat b_{ij}\rangle\langle\hat b_{ji}\rangle \\
&\equiv\hat V_F
\end{aligned}
\)</p>

With $\hat b_{ij}=\hat c_i^{\dagger}\hat c_j$ . 

After the decoupling , we can combine all these parts together with any coefficient $(0:1,1:0,1:1,\cdots)$ you like . This can be proved by variation method by doing variation of the free energy . For further details , please read [**in English**](https://physics.stackexchange.com/questions/742905/multi-channel-mean-field-theory) and [**in Chinese**](https://zhuanlan.zhihu.com/p/613087754) .

For **Hartree Fock Approximation** : $\hat H_V=\hat V_H+\hat V_F$

# 2. Extended Hubbard Model

Hubbard model is one of the most well known model in strong correlation field , it can be written as :

<p style="text-align:center">\(
\hat H_{Hub}=\sum_{ij\sigma}t_{ij}\hat c_{i\sigma}^{\dagger}\hat c_{j\sigma}+U\sum_i\hat c_{i\uparrow}^{\dagger}\hat c_{i\downarrow}^{\dagger}\hat c_{i\downarrow}\hat c_{i\uparrow}-\mu\sum_{i\sigma}\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma}
\)</p>

where $\hat c_{i\sigma}\ (\hat c_{i\sigma}^{\dagger})$ is the annihilation (creation) operator of electrons with spin $\sigma\in\left\{\uparrow,\downarrow\right\}$ ; $U$ is the coulomb potential between electrons on the same site of cristal ; $\mu$ is the chemical potential controlling the band filling . 

## 2.1. Extended Hubbard Model in Bipartite Square Lattice 

For **extended hubbard model** , we can write it as :

<p style="text-align:center">\(
\hat H_{ext}=\hat H_{Hub}+\frac{1}{2}\sum_{ij\sigma\sigma'}V_{ij}\hat c_{i\sigma}^{\dagger}\hat c_{j\sigma'}^{\dagger}\hat c_{j\sigma'}\hat c_{i\sigma}+\sum_{i\sigma}\epsilon_i\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma}
\)</p>

Where $V_{ij}$ is the coulomb potential between the electrons on site $i$ and $j$ ; $\epsilon_i$ is the staggered local potential .

To study the **bipartite square lattice** , we can simplify the model :

<p style="text-align:center">\(
\begin{aligned}
\hat H_{ext}&=\sum_{ij\sigma}t_{ij}\hat c_{i\sigma}^{\dagger}\hat c_{j\sigma}+U\sum_i\hat c_{i\uparrow}^{\dagger}\hat c_{i\downarrow}^{\dagger}\hat c_{i\downarrow}\hat c_{i\uparrow}-\mu\sum_{i\sigma}\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma}+\frac{1}{2}\sum_{ij\sigma\sigma'}V_{ij}\hat c_{i\sigma}^{\dagger}\hat c_{j\sigma'}^{\dagger}\hat c_{j\sigma'}\hat c_{i\sigma}+\sum_{i\sigma}\epsilon_i\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma} \\
&=-t\sum_{\langle ij\rangle\sigma}\hat c_{i\sigma}^{\dagger}\hat c_{j\sigma}+U\sum_i\hat c_{i\uparrow}^{\dagger}\hat c_{i\downarrow}^{\dagger}\hat c_{i\downarrow}\hat c_{i\uparrow}-\mu\sum_{i\sigma}\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma}+\frac{V}{2}\sum_{\langle ij\rangle\sigma\sigma'}\hat c_{i\sigma}^{\dagger}\hat c_{j\sigma'}^{\dagger}\hat c_{j\sigma'}\hat c_{i\sigma}-\epsilon\sum_{i\in A,\sigma}\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma}+\epsilon\sum_{i\in B,\sigma}\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma} 
\end{aligned}
\)</p>

where $t_{ij}=-t,V_{ij}=V$ when site $i$ and $j$ are neighbors , otherwise $t_{ij}=0,V_{ij}=0$ ; $\epsilon_i=-\epsilon$ when $i\in A$ , while $\epsilon_i=\epsilon$ when $i\in B$ ; $\langle ij\rangle$ means to only sum over the nearest sites .

<img src="https://raw.githubusercontent.com/Adotar/Note/main/latt2d-20230428205422765.gif" alt="img" style="zoom:40%;" />

Here is the schematic diagram of the bipartite square lattice . **From now on , all we talk about are in the half-filling bipartite square lattice . **

## 2.2. Hartree Fock Approximation of the Extended Hubbard Model

As it was mentioned in section **1.2** , we can do some decoupling and recombination to the multiplicity of the fermions to make it easier to calculate . So , the model in section **2.1** can be written as :

<p style="text-align:center">\(
\begin{aligned}
\hat H_{ext}&=-t\sum_{\langle ij\rangle\sigma}\hat c_{i\sigma}^{\dagger}\hat c_{j\sigma}+U\sum_i\hat c_{i\uparrow}^{\dagger}\hat c_{i\downarrow}^{\dagger}\hat c_{i\downarrow}\hat c_{i\uparrow}-\mu\sum_{i\sigma}\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma}+\frac{V}{2}\sum_{\langle ij\rangle\sigma\sigma'}\hat c_{i\sigma}^{\dagger}\hat c_{j\sigma'}^{\dagger}\hat c_{j\sigma'}\hat c_{i\sigma}-\epsilon\sum_{i\in A,\sigma}\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma}+\epsilon\sum_{i\in B,\sigma}\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma} \\
&\approx-t\sum_{\langle ij\rangle\sigma}\hat c_{i\sigma}^{\dagger}\hat c_{j\sigma}-\mu\sum_{i\sigma}\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma}+U\sum_{i\sigma}\bigg(\langle n_{i,-\sigma}\rangle\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma}-\frac{1}{2}\langle n_{i\uparrow}\rangle\langle n_{i\downarrow}\rangle\bigg) \\
&+V\sum_{\langle ij\rangle\sigma}\bigg[\sum_{\sigma'}\bigg(\langle n_{j\sigma'}\rangle\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma}-\frac{1}{2}\langle n_{i\sigma}\rangle\langle n_{j\sigma'}\rangle\bigg)-\frac{1}{2}\langle b_{ij\sigma}\rangle(\hat c_{i\sigma}^{\dagger}\hat c_{j\sigma}+H.c.)+\frac{1}{2}\langle b_{ij\sigma}\rangle^2\bigg] \\
\end{aligned}
\)</p>

where

<p style="text-align:center">\(
\begin{aligned}
\langle n_{i\sigma}\rangle&=\langle\hat c_{i\sigma}^{\dagger}\hat c_{i\sigma}\rangle=\frac{1}{2}+\delta n_{\sigma}\exp(i\pmb{Q}\cdot\pmb{R}_i) \\
\delta n_{\sigma}&=\frac{1}{2}(\delta n+\tau_{\sigma\sigma}^3m_z) \\
\langle b_{ij\sigma}\rangle&=\langle\hat c_{i\sigma}^{\dagger}\hat c_{j\sigma}\rangle=b_{\sigma}+\delta b_{\sigma}\exp(i\pmb{Q}\cdot\pmb{R}_i)
\end{aligned}
\)</p>

with 

<p style="text-align:center">\(
\pmb{Q}=(\pi,\pi)\ ,\ \delta n=\frac{n_A-n_B}{2}\ ,\ m_z=\frac{(n_{A,\uparrow}-n_{A,\downarrow})-(n_{B,\uparrow}-n_{B,\downarrow})}{2}
\)</p>

and the (spatially homogeneous) spin-projected bond charge $\pmb{b_{\sigma}}$ as well as its spatially modulated part $\pmb{\delta b_{\sigma}}$ . $\pmb{\tau_{\sigma\sigma}^3}$ is (1,1)-element for $\sigma=\uparrow$ or the (2,2)-element for $\sigma=\downarrow$ of the z-component of Pauli matrix .

By diagonalize it in Fourier space , we have :

<p style="text-align:center">\(
\begin{aligned}
\hat H_k&=2\sum_{k\sigma}(Vb_{\sigma}-t)(\hat c_{k\sigma}^{\dagger}\hat d_{k\sigma}+H.c.)(\cos{k_x}+\cos{k_y}) \\
&+\frac{1}{2}\sum_{k\sigma}\bigg[(U-8V)\delta n-\tau_{\sigma\sigma}^3Um_z-2\epsilon\bigg](\hat c_{k\sigma}^{\dagger}\hat c_{k\sigma}-\hat d_{k\sigma}^{\dagger}\hat d_{k\sigma}) \\
&+\bigg(\frac{U}{2}+4V-\mu\bigg)\sum_{k\sigma}\hat c_{k\sigma}^{\dagger}\hat c_{k\sigma}+\hat d_{k\sigma}^{\dagger}\hat d_{k\sigma}+Constant \\
&=\sum_{k\sigma}
\begin{pmatrix}
\hat c_{k\sigma}^{\dagger} & \hat d_{k\sigma}
\end{pmatrix}
\hat R^{\dagger}
\begin{pmatrix}
E_{k\sigma+} & 0 \\
0 & E_{k\sigma-} \\
\end{pmatrix}
\hat R
\begin{pmatrix}
\hat c_{k\sigma} \\
\hat d_{k\sigma}
\end{pmatrix}+Costant\ , \\
&\begin{cases}
E_{k\sigma\nu}=\frac{U}{2}+4V-\mu+\nu\sqrt{T_{k\sigma}^2+\Delta_{\sigma}^2}\ , \\
T_{k\sigma}=2(Vb_{\sigma}-t)(\cos{k_x}+\cos{k_y})\ , \\
\Delta_{\sigma}=(\frac{U}{2}-4V)\delta n-\frac{U}{2}\tau_{\sigma\sigma}^3m_z-2\epsilon \\
\end{cases}
\end{aligned}
\)</p>

where $\hat c_{k\sigma}^{\dagger}\ (\hat c_{k\sigma})$ is the creation (annihilation) operator for electrons on site A , while the $\hat d_{k\sigma}^{\dagger}\ (\hat d_{k\sigma})$ is the creation (annihilation) operator for electrons on site B .

Using : $F=-\frac{1}{\beta}\ln\Omega=-\frac{1}{\beta}\ln\bigg[tr\ e^{-\beta\hat H_k}\bigg]$

We have :

<p style="text-align:center">\(
f=\frac{F}{N_L}=-\frac{1}{\beta N_L}\sum_{k\sigma\nu}'\ln\bigg[1+e^{-\beta E_{k\sigma\nu}}\bigg]+\mu-\frac{U}{4}-2V+\bigg(2V-\frac{U}{4}\bigg)\delta n^2+\frac{U}{4}m_z^2-2V\sum_{\sigma}(b_{\sigma}^2+\delta b_{\sigma}^2)
\)</p>

where $\sum_{k\sigma\nu}'$ is summing over the reduced BZ of the bipartite square lattice . 

By taking variation of each order parameters $\delta n\ ,\ m_z\ ,\ b_{\sigma}$ of the Helmholtz free energy to find the minimum of $f$ , we can thus solve the **self consistent field equations .**

We have :

<p style="text-align:center">\(
\frac{\partial f}{\partial\delta n}=\frac{1}{N_L}\sum_{k\sigma\nu}'\frac{e^{-\beta E_{k\sigma\nu}}}{1+e^{-\beta E_{k\sigma\nu}}}\frac{(\frac{U}{2}-4V)\nu\Delta_{\sigma}}{\sqrt{T_{k\sigma}^2+\Delta_{\sigma}^2}}+(4V-\frac{U}{2})\delta n =0 \\
\Rightarrow \delta n=\frac{1}{N_L}\sum_{k\sigma\nu}'\frac{1}{1+e^{\beta E_{k\sigma\nu}}}\frac{\nu\Delta_{\sigma}}{\sqrt{T_{k\sigma}^2+\Delta_{\sigma}^2}}
\)</p>

As the same :

<p style="text-align:center">\(
\begin{cases}
1=\sum_{\sigma}J_{0\sigma} \\
\delta n = \sum_{\sigma}J_{1\sigma} \\
m_z=\sum_{\sigma}J_{1\sigma}\tau_{\sigma\sigma}^3 \\
b_{\sigma}=K_{\sigma} \\
\delta b_{\sigma}=0 \\
\end{cases}
\)</p>

where :

<p style="text-align:center">\(
\begin{aligned}
J_{m\sigma}&=\frac{1}{N_L}\sum_{k\nu}'n_F(E_{k\sigma\nu})\bigg[\frac{\nu\Delta_{\sigma}}{\sqrt{T_{k\sigma}^2+\Delta_{\sigma}^2}}\bigg]^m \\
K_{\sigma}&=\frac{1}{N_L}\sum_{k\nu}'n_F(E_{k\sigma\nu})\frac{\nu T_{k\sigma}(\cos{k_x}+\cos{k_y})}{2\sqrt{T_{k\sigma}^2+\Delta_{\sigma}^2}} \\
\end{aligned}
\)</p>

<p style="text-align:center">\(
n_F(E_{k\sigma\nu})=\frac{1}{1+e^{\beta E_{k\sigma\nu}}}
\)</p>

# 3. Program

To accomplish this calculation , there are several details we need to focus on , here I am going to give a brief introduction about how to calculate the self consistent field equation and what we have to be careful to .

## 3.1. Computational Logic 

Here is the main computational logic of the self consistent field equation : 

```flow
st=>start: Start
i1=>inputoutput: Input initial parameters
i2=>inputoutput: Count the mean particle number : n
i3=>inputoutput: Error
i4=>inputoutput: Change chemical potential
i6=>inputoutput: Output results of order parameters and chemical potential
cond1=>condition: Convergence or not
cond2=>condition: n=1
e=>end
st->i1->cond1
cond1(no)->i3->e
cond1(yes)->i2->cond2
cond2(no)->i4->i1
cond2(yes)->i6->e
```

## 3.2. Fourier Transformation

One should be careful when he or she is dealing with the Fourier transformation of bipatite lattice . Here is the reduced BZ of bipartite square lattice .

<img src="https://github.com/Adotar/Note/blob/main/image-20230428162100276.png?raw=true" alt="image-20230428162100276.png" style="zoom:25%;" />

We need to change the lattice into 2 sublattice , one is the sublattice just made up of atoms A , the other sublattice is just made up of atomes B . So in k-space , we need to understand that the number of k-points is the half of the number of sites in real space , which means :

<p style="text-align:center">\(
N_k=\frac{1}{2}N_L
\)</p>

## 3.3. Partical Conservation

As it was mentioned in section **2.1** , the model we care about is a **half-filling** extended Hubbard model , which means the average of the number of particles is **1** :

<p style="text-align:center">\(
n=\frac{1}{N_L}\sum_{i\sigma}\langle n_{i\sigma}\rangle=1
\)</p>

To use this property of the model , we should find a qualified chemical potential $\mu$ each time we have the convergence result of the order parameter under a certain parameter is calculated . After we have the result , we should count the mean particle number $n$ and see if it is **1** . If it is then output the result , if it is not , change the chemical potential . But how to change the chemical potential . First we need to understand that all of the sites that is occupied is under the chemical potential , so if $n>1$ , which means $\mu$ is a little bit large , we just need to reduce the chemical potential until $n=1$ . Vice versa , if $n<1$ , enlarge $\mu$ .

# 4. Result

## 4.1. Phase Diagram

<img src="./Fortran/2nd.Master/extended-Hubbard/mean-field/Phase%20Diagram/Phase2/PhaseDiagram.jpeg" alt="PhaseDiagram" style="zoom:15%;" />

Here is the phase diagram of the extended hubbard model approximated by mean field theory at zero temperature . $CO$ phase is charge-order phase , $SCO$ phase is spin-charge-order phase . $CO$ phase is a phase where $m_z\equiv0$ , no matter what the initial value of the order you input , which is also called **charge density wave phase (CDW)** . $CO^*$ phase is a phase where the ground state is CDW while **spin density wave (SDW)** is also a solution of the self consistent equition . Vice versa , $SCO^*$ phase is a phase where the ground state is SDW , while there is a CDW solution . **This diagram satisfies our physical guess that large $U$ enlarges SDW while large $\epsilon$ enlarges CDW .**

**How do we distinguish whether it is a CDW or a SDW through the solution of the equation ? **Find the out put of the order parameters . $\delta n$ represents the CDW while $m_z$ represents the SDW . If $\delta n\neq0$ , means there is a CDW . If $m_z\neq0$ , means there is a SDW . 

**How do we distinguish which one is the ground state ?** By putting in different initial value of $(\delta n,m_z)$ , we will get different result of the consistent equation in the same of other parameters . Then , calculate the Helmholtz free energy and see which one of the different initial value is the smallest . The smallest one represents the ground state . That is how we distinguish the $CO^*$ phase and $SCO^*$ phase .

**How do we distinguish the pure state of CDW ?** The pure state of CDW means no matter what the initial value of order parameters you give , the convergent solution is $\delta n\neq0,m_z=0$ .That means there is not a SDW solution in this region .

One should be noticed is that when $\epsilon=0$ , $\delta n\equiv0$ . So , when $U/t>4$ , there is a solution of pure SDW .

### 4.2. Band Structure near the Phase Transition Point

<img src="https://raw.githubusercontent.com/Adotar/Note/main/Dispersion.jpg" alt="Dispersion" style="zoom:80%;" />

Here is the band structure near the phase transition point $(U/t=4.6,\epsilon/t=0.24)$ . The red line represents the result state is CDW , while the blue one represents the state of SDW . We can easily figure out that the grount state at this point is SDW . Because the model is half-filling , all of the state occupied is under $0$ . Because of the spin , the band of $SCO$ is splitted into two bands with different energy , while both two band of $CO$ have the same energy . So the total energy of $SCO$ is smaller than that of $CO$ . **The ground state is $SCO$ ** .

 ## 4.3. Order Parameters

In this diagram , we can see the result of order parameters changing with the $\epsilon$ $(U/t=4.6\ or \ 4.2,V/t=1)$ . We can see a discontinuing jump in both pictures , which represent the phase transition point . Also , we should notice that $\delta n\neq0$ when $\epsilon\neq0$ , so in the ground state of $SCO$ phase , CDW is also exist . But $m_z=0$ when it goes into $CO$ phase , which means there is not any SDW in this phase . Last but not least , the discontinuous jump of order parameters represents the first order phase transition . 

<img src="https://raw.githubusercontent.com/Adotar/Note/main/Result.jpg" alt="Result" style="zoom:100%;" />
