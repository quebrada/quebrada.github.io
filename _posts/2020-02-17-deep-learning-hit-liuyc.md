---
layout: post
title: 深度学习基础 - 哈尔滨工业大学 - 刘远超
date: 2020-02-17
categories: Deep-learning
tags: Deeplearning
status: publish
type: post
published: true
author: Quebradawill
---

## 第一讲：深度学习概述

### 1.1 深度学习的引出

### 1.2 数据集及其拆分

1、类别标签的 ground truth 与 gold standard：

- ground truth：可翻译为地面实况等。在机器学习领域一般用于表示真实值、 标准答案等，表示通过直接观察收集到的真实结果。<br>
- gold standard：可翻译为金标准。医学上一般指诊断疾病公认的最可靠的方法。<br>
- 在机器学习领域，更倾向于使用“ground truth” 。 而如果用 gold standard 这个词，则表示其可以很好地代表 ground truth。

2、训练集（training set）、测试集（testing set）和验证集（validation set）：

- 训练集用来训练模型，即被用来学习得到系统的参数取值。<br>
- 测试集用于最终报告模型的评价结果，因此在训练阶段测试集中的样本应该是 unseen 的。<br>
- 有时把训练集进一步划分为训练集和验证集。验证集与测试集类似，也是用于评估模型的性能。**区别**是验证集主要用于<font color='blue'>模型选择</font>和<font color='blue'>调整超参数</font>，因而一般不用于报告最终结果。

3、网格搜索调超参数

超参数是指在学习过程之前需要设置其值的一些变量。

网格搜索：

- 假设模型有两个超参数：$A$ 和 $B$。$A$ 的可能取值为 $\{ a1, a2, a3\}$，$B$ 的可能取值为连续的，如在区间 $[0, 1]$，由于 $B$ 值连续，通常对其离散化，如变为 $\{ 0, 0.25, 0.5, 0.75, 1\}$；<br>
- 如果使用网格搜索，就是尝试各种可能的 $(A,B)$ 值对，找到能使模型取得最高性能的 $(A,B)$ 值对。

网格搜索与 K 折交叉验证结合调整超参数的具体**步骤**：

- 确定评价指标；<br>
- 对于超参数取值的每种组合，在训练集上使用交叉验证的方法求得其 K 次评价的性能均值；<br>
- 最后，比较哪种超参数取值组合的性能最好，从而得到最优超参数的取值组合。

### 1.3 分类及其性能度量

### 1.4 回归问题及其性能评价

1、常用的<font color='blue'>评价回归问题</font>的方法

- 平均绝对误差 MAE（mean absolute error）；<br>
- 均方误差 MSE（mean squared error）及均方根差 RMSE；<br>
- Log loss，或称交叉熵 loss（cross-entropy loss）；<br>
- R 方值，确定系数（r2 score）。

### 1.5 一致性的评价方法

1、一致性评价：是指对两个或多个相关的变量进行分析，从而衡量其相关性的密切程度。

2、皮尔森相关系数（Pearson coefficient）法

应用背景：

- 用来衡量两个用户之间兴趣的一致性；<br>
- 用来衡量预测值与真实值之间的相关性；<br>
- 既适用于<font color='blue'>离散</font>的、也适用于<font color='blue'>连续</font>变量的相关分析。

计算公式：


$$
\rho_{X,Y} = \frac{\textrm{cov}(X,Y)}{\sigma_X \sigma_Y} = \frac{E[(X - \mu_X)(Y - \mu_Y)]}{\sigma_X \sigma_Y}
$$


皮尔森相关系数的取值区间为 $[-1, 1]$。

3、Cohen‘s kappa 相关系数

也可用于衡量两个评价者之间的一致性。其特点在于：

- 与 Pearson 相关系数的区别：Cohen‘s kappa 相关系数通常用于<font color='blue'>离散</font>分类的一致性评价；<br>
- 其通常被认为比两人之间的简单一致百分比<font color='blue'>更强壮</font>，因为 Cohen‘s kappa考虑到了二人之间的随机一致的可能性；<br>
- 如果评价者多于 2 人时，可以考虑使用 <font color='blue'>Fleiss' kappa</font>。

4、Fleiss' kappa

## 第二讲：特征工程概述

### 2.1 特征工程

1、Feature engineering is the process of using domain knowledge of the data to create features that make machine learning algorithms work.

2、<font color='blue'>数据</font>和<font color='blue'>特征</font>决定了机器学习的**上限**，而<font color='blue'>模型</font>和<font color='blue'>算法</font>只是**逼近**这个上限而已。

### 2.2 向量空间模型及文本相似度计算

### 2.3 特征处理（特征缩放、选择及降维）

1、特征缩放

**特征值缩放（Feature Scaler）**也可以称为<font color='blue'>无量纲处理</font>。 主要是对每个列，即同一特征维度的数值进行规范化处理。

应用背景：

- 不同特征（列）可能不属于同一量纲，即特征的规格不一样。例如，假设特征向量由两个解释变量构成，第一个变量值范围 $[0,1]$，第二个变量值范围 $[0,100]$。<br>
- 如果某一特征的方差数量级较大，可能会主导目标函数，导致其他特征的影响被忽略。

常用方法：

- 标准化法<br>
- 区间缩放法

标准化法的前提是特征值服从<font color='blue'>正态</font>分布。公式表达为


$$
X_{\textrm{scale}} = \frac{X - \bar{X}}{\sigma_X}
$$


区间缩放法利用了边界值信息，将特征的取值区间缩放到某个特定范围。假设 $\max$ 和 $\min$ 为希望的调整后范围，则


$$
X_{\textrm{scaled}} = \frac{X - X_{\min}}{X_{\max} - X_{min}} \times (\max - \min) + \min
$$


特征值的<font color='blue'>归一化</font>或称<font color='blue'>规范化（Normalizer）</font>是依照特征矩阵的行（样本） 处理数据，其目的在于样本向量在点乘运算或计算相似性时，拥有统一的标准，也就是说都转化为“单位向量”。 即使每个样本的范式（norm）等于 1。

L1 norm 归一化：


$$
x_i^{'} = \frac{x_i}{\sum_{j=1}^n \vert x_j \vert}, \quad i = 1, 2, \cdots, n
$$


L2 norm 归一化：


$$
x_i^{'} = \frac{x_i}{\sqrt{\sum_{j=1}^n x_j^2}}, \quad i = 1, 2, \cdots, n
$$

2、特征选择

为什么要进行特征选择？1）降维以提升模型的效率；2）降低学习任务的难度；3）增加模型的可解释性。

特征选择的角度：

- 特征是否<font color='blue'>发散</font>：对于不发散的特征，样本在其维度上差异性较小；<br>
- 特征与目标的<font color='blue'>相关性</font>：应当优先选择与目标相关性高的特征。

几种常见的特征选择方法：

- 方差选择法<br>
- 皮尔逊相关系数法<br>
- 基于森林的特征选择法<br>
- 递归特征消除法

方差选择法的原理：方差非常小的特征维度对于样本的区分作用很小，可以剔除。

## 第三讲：回归问题及正则化

### 3.1 线性回归模型及其求解方法  

1、线性模型

- 狭义线性（linear）模型<br>
  - 通常指自变量与因变量之间按比例、成直线的关系，在数学上可理解为一阶导数为常数的函数，如 $y = \theta^T x$；<br>
  - 线性通常表现为一次曲线。<br>
- 广义线性（generalized linear model，GLM ）<br>
  - 是线性模型的扩展，主要通过<font color='blue'>联结函数</font> $𝑔(\cdot)$ （link function），使预测值落在响应变量的变幅内。例如逻辑回归 $h_{\theta}(x) = g(\theta^T x) = 1 / (1 + e^{- \theta^T x})$（括号内为线性函数）

2、非线性模型

- 非线性模型一般指不按比例、不成直线的关系，一阶导数不为常数；<br>
- 常见的非线性模型<br>
  - 2 次及 2 次以上的多项式 $ y = a_n x^n + a_{n-1} x^{n-1} + \cdots + a_1 x + a_0$；<br>
  - 幂函数模型 $ y = \beta_0 x_1^{\beta_1} x_2^{\beta_2} \cdots x_k^{\beta_k}$；
  - 指数函数模型 $y = \beta_0 e^{\beta_1 x}$；
  - 对数函数模型 $y = \beta_0 + \beta_1 \log x$；
  - 等等

### 3.2 多元回归与多项式回归

### 3.3 损失函数的正则化

### 3.4 逻辑回归

## 第四讲：信息熵及梯度计算

### 4.1 信息熵

### 4.2 反向传播中的梯度

### 4.3 感知机

## 第五讲：循环神经网络及其变体

### 5.1 循环神经网络

1、什么是循环神经网络？传统神经网络模型，隐藏层的节点之间是<font color='blue'>无连接</font>的；循环神经网络（Recurrent Neural Network，RNN）的隐藏层的节点之间<font color='red'>有连接</font>，是主要用于对**序列**数据进行分类、预测等处理的神经网络。

2、RNN 的参数共享：传统神经网络中，每一层的参数是<font color='blue'>不共享</font>的；而在 RNNs 中，每一步（每一层）都<font color='red'>共享参数</font>。

### 5.2 长短时记忆网络（Long Short-Term Memory）

1、标准 RNN 可以处理不太长的相关信息间隔；但标准 RNN 无法处理更长的上下文间隔，即<font color='blue'>长期依赖</font>问题。长短期记忆网络，是 RNN 的扩展，其通过特殊的结构设计来避免长期依赖问题。

### 5.3 双向循环神经网络和注意力机制（Bidirectional RNN and Attention Mechanism）

1、在很多应用中，当前步，即第 $t$ 步的输出与<font color='blue'>前面</font>的序列和<font color='blue'>后面</font>的序列都有关。

2、注意力模型（机制）是受到了人类注意力机制的启发。

## 第六讲：卷积神经网络

### 6.1 卷积与卷积神经网络

1、<font color='red'>卷积神经网络</font>具有以下特点：1）局部卷积，2）参数共享，3）多卷积核，4）池化操作，5）多层处理。

2、<font color='red'>池化</font>的优点：1）降维；2）克服过拟合；3）在图像识别领域，池化还能提供平移和旋转不变性。

3、一般而言，在图像处理中，一层卷积及降采样往往只学到了局部的特征。**层数越多，学到的特征越全局化。**因此通过这样的多层处理，低级的特征组合形成更高级的特征表示。

### 6.2 LeNet-5 模型分析

## 第七讲：递归神经网络

### 7.1 情感分析及传统求解方法

### 7.2 词向量

### 7.3 递归神经网络及其变体（Recursive Neural Network and Its Variants）

**注意：**循环神经网络（<font color='red'>Recurrent</font> Neural Network，RNN）和递归神经网络（<font color='blue'>Recursive</font> Neural Network）。

## 第八讲：生成式神经网络

### 8.1 自动编码器（Autoencoder）

1、自动编码器

自动编码器是一种无监督的神经网络模型，其目标是通过训练网络<font color='blue'>忽略信号“噪声”</font>，从而学习得到数据的低维度表示（编码）。通常分为两步：<br>1）学习到输入数据的隐含特征，即编码（coder）$\phi : x \to z$；<br>
2）用隐含特征重构原始的输入数据，即解码（decoder）$\psi: z \to x$。

2、堆栈自动编码器本质上就是<font color='blue'>增加</font>中间特征层数。

### 8.2 变分自动编码器（Variational Autoencoder）

### 8.3 生成对抗网络（Generative Adversarial Networks）

1、判别式模型和生成式模型

假设研究对象的观测变量为 $X$，类别变量为 $Y$，则：

- 判别式模型（Discriminative models，或 Conditional models）<br>
  - 按照一定的判别准则，从数据中直接学习决策函数 $Y = f(X) $ 或者条件概率分布 $ P(Y \vert X; \theta)$ 作为预测的模型；<br>
  - 典型的判别模型包括：$k$ 近邻法、决策树、最大熵模型、支持向量机等。<br>
- 生成式模型（Generative models）<br>
  - 从数据中学习联合概率分布 $P(X,Y)$，之后可以转变为 $P(Y \vert X)$ 作为预测的模型，例如利用条件概率分布 $ P(Y \vert X) = P(X,Y) / P(X) $；<br>
  - 典型的生成模型包括：朴素贝叶斯法、混合高斯模型、马尔可夫模型等。

**判别式**模型：只是对给定的样本进行分类。不关心数据如何生成。**生成式**模型：根据生成假设，哪个类别最有可能生成这个样本？

2、生成对抗网络 GAN 的基本原理

GAN（Generative Adversarial Networks）包括两部分：<font color='blue'>生成器</font>和<font color='blue'>判别器</font>。

- 生成器：从随机噪声中生成图像（随机噪声通常从均匀分布或高斯分布中获取）；<br>
- 判别器：其输入为生成器生成的图像和来自训练集中的真实图像，并对其进行判别。得到输出值为一个 $0$ 到 $1$ 之间的数，表示图像为真实图像的概率，real 为 $1$，fake 为 $0$。