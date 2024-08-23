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

# 基本术语与模型评估

## 基本术语  

前一节中我们已经明确了机器学习中的核心概念：**数据** (data) 、**模型** (model) 和**学习** (learning) ，接下来我们明确一下它们的数学表示，以便我们用更为严谨的数学语言展开接下来的讨论。\alpha

>

- **data**：数据，用向量$\alpha$表示
- **model**：模型，通过统计学或优化理论获得
- **learning**：学习，通过优化理论学习模型参数 
  {: .prompt-tip }

在获得训练数据时，我们通常需要区分训练集 (training set) 和测试集 (testing set)，训练集是用于训练或拟合模型，获得模型参数，测试集是用于评估模型泛化能力。二者之间不能有交集，避免数据泄露问题。

## 机器学习流程

机器学习的流程因具体问题而确定，但大致可以归纳为如下框架：

- **数据预处理**：对数据进行清洗、转换和特征提取，转换为合适的数据类型，以便于后续的模型训练。
- **定义模型**：根据问题的性质选择合适的机器学习模型，例如线性回归、logistic 回归、softmax 回归、决策树、支持向量机、神经网络等。
- **初始化模型参数**：根据问题的性质合理设置初始化参数，可以采取随机数或基于经验或已有模型。
- **定义损失函数**：为模型训练参数提供方向，常用的损失函数有平方损失函数、交叉熵损失函数。
- **定义优化算法**：常用的优化算法有 LMS、LWR 等。
- **模型训练**：使用训练集中的数据对模型进行训练，使其能够从数据中学习到相关的模式和规律。
- **模型预测**：使用独立于训练数据的测试集中的数据来评估模型的泛化性。

## 机器学习分类

首先基于上面的描述，总结一些机器学习中的关键组件，无论什么类型的机器学习问题，都会遇到这些组件：

>

- 可以用来学习的数据 (data)
- 如何转换数据的模型 (model)
- 一个目标函数 (objective function)，用来量化模型的有效性
- 调整模型参数以优化目标函数的算法 (algorithm) 
  {: .prompt-tip }

按照数据是否有标签 (label)，我们可以大致将机器学习问题分为**监督学习** (Supervised Learning)、**无监督学习** (Unsupervised Learning)，在后续的学习中我们还会遇到将两种学习方法相结合的半监督学习，以及**强化学习** (Deep Reinforcement Learning)。我们将首先将目光放在以下几类问题上。如下图所示

![image](https://github.com/user-attachments/assets/9aa5eaa5-3f68-43a7-9648-a506cc9d5c4e)


**Reference**

* Mathematics For Machine Learning