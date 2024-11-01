---
title: Basic Terminology and Model Evaluation
description: Basic terminology and model evaluation
author: longyuan
date: 2024-08-23 
categories: [Artificial Intelligence, Machine Learning]
tags: [machine learning]
pin: true
math: true
mermaid: true
image:
  path: /assets/ml.jpg

---

## 基本术语与模型评估

### 基本术语

前一节中我们已经明确了机器学习中的核心概念：**数据** (data)、**模型** (model) 和 **学习** (learning)，接下来我们明确一下它们的数学表示，以便我们用更为严谨的数学语言展开接下来的讨论。

一般地，数据用向量 $\boldsymbol{x}$ 表示，样本 (example) 用 $(\boldsymbol{x}, y)$ 表示，其中 $y$ 为标签 (label)，可能未知。数据集 (dataset) 用 $D = ${$(\boldsymbol{x_1}, y_1), (\boldsymbol{x_2}, y_2), \ldots, (\boldsymbol{x_m}, y_m)$}表示，每个数据含 $d$ 个特征 (feature)，用 $\boldsymbol{x_i} = (x^1_i, x^2_i, \ldots, x^d_i)$ 表示，$d$ 称为数据的维数 (dimensionality)。模型可以分为决策模型和概率模型，它们都依赖于相应的参数 $\boldsymbol{\theta}$。决策模型通常用一个映射来表示，记为：

$$
f: \mathcal{X} \to \mathcal{Y}
$$

$$
\boldsymbol{x} \mapsto y
$$

引入参数后，决策模型可以表示为：

$$
f(\boldsymbol{x}) = f(\boldsymbol{x}, \boldsymbol{\theta})
$$

对于概率模型，我们通常可以用一个概率分布来描述数据集中样本的分布情况。所以，我们的论述将基于数理统计学中的参数统计推断和非参数统计推断方法。

一般地，我们讨论的数据集通常取值为实数，为了刻画数据的分布或者相似程度，我们需要引入度量，所以我们一般在度量空间中讨论问题，如果该度量存在对应的范数，该度量空间便成为一个（实）赋范空间。

### 模型评估

对于决策模型，随着模型参数 $\boldsymbol{\theta}$ 变化，会产生一系列映射，这些映射构成一个函数簇 $\mathscr{F} = ${$f(\boldsymbol{x}, \boldsymbol{\theta}) : \boldsymbol{\theta} \in \Theta$}，$\Theta$ 为参数空间。决策模型的预测问题一般是通过优化（数学规划）方法来获得点估计（point estimator）。

对于概率模型，随着模型参数 $\boldsymbol{\theta}$ 变化，会产生一系列分布，这些分布构成一个分布簇 $\mathscr{F} = ${$f(\boldsymbol{x}, \boldsymbol{\theta}) : \boldsymbol{\theta} \in \Theta$}，$\Theta$ 为参数空间，$f(\boldsymbol{x}, \boldsymbol{\theta})$ 为概率函数。概率模型的推断问题可以采取点估计，也可以采取贝叶斯推断。

一般地，机器学习的目标，就是从模型簇中寻找最佳的参数，使得模型的效果最好。而学习过程，便是在可行域即参数空间中搜索参数的优化（数学规划）问题。为了达到这一目标，我们首先要明确如何衡量一个模型的优劣，这便是本节的核心，模型评估问题。

对于决策模型，我们需要度量模型预测值与真实值之间的差异，为此，我们在实数域上引入度量 $d$，满足正定性、对称性和三角形不等式。而模型的优劣，可以用损失函数 $L$ 表示：

$$
L = \frac{1}{m} \sum_{i=1}^{m} d(y_i, \hat{y}_i)
$$

其中 $\hat{y}_i = f(\boldsymbol{x}_i, \boldsymbol{\theta})$，对于连续情形，

$$
L = \int d(y, \hat{y}) p(\boldsymbol{x}) \, \text{d}\boldsymbol{x}
$$

其中 $\hat{y} = f(\boldsymbol{x}, \boldsymbol{\theta})$。总的概括为：

>
$$
L = \mathbb{E}_{\boldsymbol{x} \in \mathcal{D}} [d(y, \hat{y})]
$$
{: .prompt-tip }

而我们的模型评估及选择，就是为了最小化损失函数。因此，我们的机器学习问题便转化成了如何用合适而高效的算法来学习，达到最小化损失函数的优化问题，即：

$$
\text{argmin}_{\boldsymbol{\theta} \in \Theta} L(f, \mathcal{X}, \mathcal{Y})
$$

用矩阵的语言表述，令 $\boldsymbol{X} := (\boldsymbol{x_1}, \boldsymbol{x_2}, \ldots, \boldsymbol{x_m})^T$，$\boldsymbol{y} := (y_1, y_2, \ldots, y_m)^T$，则有：

>
$$
\text{argmin}_{\boldsymbol{\theta} \in \Theta} L(f, \boldsymbol{X}, \boldsymbol{y})
$$
{: .prompt-tip }




**Reference**

* Mathematics For Machine Learning
* 机器学习 周志华

**许可协议**


![alt text](../assets/ccbyncnd.png)
