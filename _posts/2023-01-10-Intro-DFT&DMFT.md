---
layout: post
read_time: true
show_date: true
title: "DFT+DMFT简介"
date: 2023-01-09
img: posts/20210420/post8-rembrandt.jpg
tags: [凝聚态物理, DFT, DMFT]
category: opinion
author: Adotar
mathjax: yes
description: "在凝聚态物理中，我们经常使用DFT（密度泛函理论）进行第一性原理计算，从而预测物质性质。然而，在具有电子强相互作用的体系中，DFT并不能完全计算出体系的所有性质。因此我们需要新的方法来计算并预测强关联体系的物理性质。"
---
## 1. 为什么需要DFT+DMFT

在凝聚态物理中，我们经常使用DFT（密度泛函理论）进行第一性原理计算，从而预测物质性质。然而，在具有电子强相互作用的体系中，DFT并不能完全计算出体系的所有性质。因此我们需要新的方法来计算并预测强关联体系的物理性质。

## 2. 计算模型与原理

DFT+DMFT（动力学平均场理论）是一个用来计算强关联体系的有效方法。

### 2.1 DFT

科恩-沈吕九的密度泛函理论中最关键的思想是通过引入电子密度 $ \rho(\vec{r}) $ ，从而将原本具有相互作用的电子原子体系问题转化为无相互作用问题。DFT定义了一个有效库伦势 $ V_c(\vec{r}) $ 如下：

<p style="text-align:center">\(<br>
\begin{align}
\begin{split}
V_c(\vec{r})=V(\vec{r})+\int \frac{\rho(\vec{r'})}{|\vec{r}-\vec{r'}|}d\vec{r'}
\tag{1}
\end{split}
\end{align}
\)</p>

（1）式中 $V(\vec{r})$ 是离子势能函数，等式右边第二项为体系所有电子在空间 $\vec{r}$ 位置产生的总势能。除此之外，DFT还定义了交换关联函数 $V_{xc}$ ，并且列出了电子密度为目标解的自洽方程：

<p style="text-align:center">\(<br>
\begin{align}
\begin{split}
\bigg[-\frac{1}{2}\nabla^2+V_c(\vec{r})+V_{xc}(\vec{r})-E_i\bigg]\psi_i(\vec{r})=0
\tag{2}
\end{split}
\end{align}
\)</p>

<p style="text-align:center">\(<br>
\begin{align}
\begin{split}
\rho(\vec{r})=\sum_i|\psi_i(\vec{r})|^2
\tag{3}
\end{split}
\end{align}
\)</p>

这里的 $\psi_i$ 是无相互作用的科恩-沈吕九（KS）波函数。通过设置一个初始电子密度 $ \rho(\vec{r}) $ 代入（1）式，计算出初始的有效库伦势 $V_c(\vec{r})$ ，再代入（2）式计算出科恩-沈吕九准粒子的本征波函数 $\psi_i$ ，最后通过（3）式对其所有本征态求和，从而计算出第一次迭代解出的新的电子密度 $ \rho(\vec{r}) $ 。然后将其再次代入（1）式，进入第二次的迭代，依次循环，进行多次迭代。然而（2）式中的交换关联函数 $V_{xc}$ 是未知的。 $V_{xc}$ 的值取决于整个空间的电子密度分布，通常我们将其近似为只与 $\vec{r}$ 位置的电子密度相关的函数。虽然在弱相互作用体系中， $V_{xc}$ 相比于 $ V_c(\vec{r}) $ 的值要小很多，但是在强关联体系下，我们对 $V_{xc}$ 的近似会在迭代过程中带来极大的误差，甚至会出现物理上的错误。

### 2.2 DMFT

当固体中原子的最外层电子为s或者p轨道电子时，由于不同原子间s和p电子轨道的交叠积分较大，电子是高度共享的，电子动能远大于库伦相互作用能，我们在计算（2）式时能够忽略 $ V_c(\vec{r}) $ 和 $V_{xc}$ ，误差较小。当固体中原子的最外层电子为d或者f轨道电子时，他们较小的轨道交叠积分，会让电子表现出较强的局域现象，电子只会在离子附近运动，动能较小，从而使得 $ V_c(\vec{r}) $ 和 $V_{xc}$ 不能被忽略， $V_{xc}$ 的误差将会对DFT的结果有较大的影响。所以，我们需要新的计算方法来表征强关联的物理现象。

早期人们理解强关联体系主要通过Hubbard模型，此模型的哈密顿量如（4）式所示，由格点间电子跃迁项和同一格点自旋相反的电子库伦排斥项组成：

<p style="text-align:center">\(<br>
\begin{align}
\begin{split}
\hat{H}=\sum_{ij,\sigma}t_{ij}c^{\dagger}_{i\sigma}c_{j\sigma}+U\sum_in_{i\uparrow}n_{i\downarrow}
\tag{4}
\end{split}
\end{align}
\)</p>

其中 $c^{\dagger}_{i\sigma}$ 和 $c_{i\sigma}$ 是第 $i$ 个格点上自旋为 $\sigma$ 的电子的产生和湮灭算符， $t_{ij}$ 是第 $j$ 个格点电子跃迁到第 $i$ 个格点上的格点间跃迁振幅， $U$ 是局域库伦排斥势能。如图1所示，当 $U\gg t$ 时，电子关联作用较强，原本的能带理论不再适用，可能使得按照经典方法计算出为金属的固体在依照（4）式的计算下转变成了绝缘体<sup><a href="#ref1">1</a></sup>。这种金属到绝缘体的改变，是传统的DFT无法预测出来的。

一维的Hubbard模型可以精确求解<sup><a href="#ref2">2</a></sup>，然而二维和三维的Hubbard模型只能通过数值方法计算。随着体系中格点数目的增加，计算量呈指数型增涨，即使如今使用超算也很难计算出结果。1992年，Georges和Kotliar两人发现Hubbard模型在无穷维极限下是精确可解的，并且将其与自洽的单格点量子杂质模型类比，为DMFT方法打下了基础<sup><a href="#ref3">3</a></sup>。DMFT关键的思想是将相互关联的多体问题转化为求解安德森杂质模型，其哈密顿量为：

<p style="text-align:center">\(<br>
\begin{align}
\begin{split}
\mathcal{H}_{AIM}=\mathcal{H}_{atom}+\sum_{\nu,\sigma}\epsilon^{bath}_{\nu}n^{bath}_{\nu,\sigma}+\sum_{\nu,\sigma}(V_{\nu}c^{\dagger}_{0,\sigma}a^{bath}_{\nu,\sigma}+h.c.)
\tag{5}
\end{split}
\end{align}
\)</p>

（5）式中， $\mathcal{H}_{atom}$ 表示与杂质格点上的原子自由度相关的能量， $\epsilon^{bath}_{\nu}$ 是无相互作用电子池的能级， $n^{bath}_{\sigma}=c^{\dagger}_{\sigma}c_{\sigma}$ 是自旋为 $\sigma$ 的电子密度 ， $V_c$ 是电子在杂质原子与无相互作用电子池之间交换的概率幅 。我们定义与频率相关的杂化函数 $\Delta(\omega)$ ：

<p style="text-align:center">\(<br>
\begin{align}
\begin{split}
\Delta(\omega)=\sum_{\nu}\frac{|V_{\nu}|^2}{\omega-\epsilon^{bath}_{\nu}}
\tag{6}
\end{split}
\end{align}
\)</p>

（6）式中的杂化函数 $\Delta(\omega)$ 决定了电子在杂质格点和无相互作用电子池之间跃迁的能力。理论上， $\Delta(\omega)$ 越大，电子越被整个体系共享； $\Delta(\omega)$ 越小，电子运动越是局域。与DFT相比，DFT通过LDA（局域密度近似）或者GGA（广义梯度近似）[^1]等方法方法近似交换关联函数 $V_{xc}$ ，而DMFT是通过计算 $\Delta(\omega)$ 来表征强关联体系的相互作用强度。

  <center>
    <img src="https://raw.githubusercontent.com/Adotar/Note/main/Band-diagram-of-Mott-Hubbard-Insulator-reproduced-from-Ref67.jpg?token=A5EYVQCGDRSMUY55775RJ43DXPVTU"
       style="zoom:50%;" />
    <br>
    <table>
      图1 Hubbard带的形成原理
    </table>
  </center>

### 2.3 DFT+DMFT

尽管DMFT在计算强关联体系时，相较于DFT有较强的优势，但是它并不能直接用于计算真实材料。为了计算真实材料，我们需要将DMFT与类似于DFT等第一性原理计算方法连接连接起来，因此而诞生了DFT+DMFT计算方法。如图2所示，DFT+DMFT迭代除了履行经典的DFT迭代外，还增加了计算格林函数 $G(\omega,\vec{r},\vec{r}')$ ，杂化函数 $\Delta(\omega)$ ，自能 $\sum(\omega)$ 的迭代[^2]。在每一次的DFT迭代后，将计算出的KS波函数作为DMFT的输入，计算得到初始 $G(\omega,\vec{r},\vec{r}')$ ，然后实行图2中的绿色迭代部分，等待迭代自洽后，将得到的末态 $G(\omega,\vec{r},\vec{r}')$ 作为DFT下一次迭代中计算电子密度 $\rho(\vec{r})$ 的输入。

<center>
  <img src="https://raw.githubusercontent.com/Adotar/Note/main/DFT%2BDMFT loop.png?token=A5EYVQGDCYJJCGLGBDQ3W5LDXPVDS" />
  <br>
  <table>
    图2 DFT+DMFT迭代
  </table>
</center>


## 3. 应用

Kristjan Haule和Turan Birol使用DFT+DMFT方法计算了莫特绝缘体相变金属氧化物FeO的自由能与晶胞体积，以及内能与晶胞体积的关系[^3]。如图3（a）所示，300K时，通过自由能F和内能E计算的FeO平衡晶格体积分别为20.24 $\AA^3$ 和20.28 $\AA^3$ ，相较于实验测量的20.342 $\AA^3$ 分别小了0.16%和0.10%。本次通过DFT+DMFT计算的结果相比于之前使用经典DFT的计算结果精确度有很大提升，例如：PBE-sol相较于实验值小5.2%，PBE为5.0%，LDA为7.7%[^4]。图3（b）中，展示了FeO在300K时不同压强下的晶胞体积，可见其数值计算结果与实验值极为吻合[^5]。

<center>
  <img src="https://raw.githubusercontent.com/Adotar/Note/main/91EFA3B0BFB4DE5EB560BBE2C90DA02C.png?token=A5EYVQGUVQ7AQ5NSSKKY3V3DXPVW6" style="zoom:40%;" />
  <br>
  <table>
    图3 （a）300K，DFT+DMFT计算FeO自由能和内能与晶胞体积的关系；
    <br>
    （b）300K，FeO晶胞体积和压强的关系。
  </table>
</center>


## 4. 科学创新的结论

DFT+DMFT通过对电子间强相互作用的有效近似，能够有效解决经典DFT计算无法准确求解的部分强关联问题，使得人们对于强关联电子体系有了更深刻的认识。



[^1]: LDA是将 $V_{xc}(\vec{r})$ 近似为只与 $\rho(\vec{r})$ 相关的函数，GGA是将$V_{xc}(\vec{r})$ 近似为与 $\rho(\vec{r})$ 和 $\nabla\rho(\vec{r})$ 相关的函数。
[^2]: [Arpita Paul, Turan Birol. Application of DFT+DMFT in Materials Science. Anuu. Rev. Mater. Res. 2019.49:31-52.](https://www.annualreviews.org/doi/10.1146/annurev-matsci-070218-121825) 
[^3]: [Kristjan Haule, Turan Birol. Free Energy from Stationary Implementation of the DFT+DMFT Functional. Phys. Rev. Lett. 115, 256402 (2015).](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.115.256402) 
[^4]: 这三种方法均为经典DFT+U这一类方法，只有赝势取值不同这一区别。
[^5]: 黑点和白点分别为[T. Yagi](http://dx.doi.org/10.1029/JB090iB10p08784)以及[R. L. Clendenen](http://dx.doi.org/10.1063/1.1726610)的实验结果。
