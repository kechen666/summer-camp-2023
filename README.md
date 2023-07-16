# 量子金融项目

## 任务布置

选取任意任务完成，若时间足够可进一步探索拓展内容，编程语言不限。最后需要提交任务报告（Markdown、LaTeX、Word文档皆可），并准备最后阶段的汇报。**可围绕任务设计实验，把一切所思所想和实验结果写进报告；即使时间关系没有完成任务，也建议把所有所做的工作写进报告**。

- 量子计算软件包：Qiskit、TensorCircuit
- 量子金融软件包：Qiskit Finance

### 任务：量子金融算法的进阶优化——组合优化问题

> 难点：约束处理、参数更新
>
> 难度：中级

我们通过调整电路上的参数来使得测量得到的结果最好。`example2`中展示了一个使用参数化电路求函数最值的简单例子，虽然利用参数化电路解决`example2`中的问题显得多此一举，但有助于同学们理解参数化电路的思想。参数化量子电路是变分量子算法（VQE、QAOA等）的重要组成部分，在面对复杂的组合优化问题时能体现量子优势。

投资组合优化问题可表示为一个最优化问题。

$$
\begin{aligned}
\min_{x \in \{0, 1\}^n}\quad&  q x^T \Sigma x - \mu^T x\\
\text{s.t. }\quad& 1^T x = B
\end{aligned}
$$

**你需要做：**

1. 假设上式约束不存在，求最小值；
2. 上式约束存在，求最小值。

若自行构建电路并调整参数，可尝试：

- 梯度下降
- 群体智能
- 常用的优化器（如scipy.optimize）

也可直接利用常用的量子变分算法QAOA、VQE等。

参考资料：

- [IBM® Decision Optimization CPLEX® Modeling for Python](http://ibmdecisionoptimization.github.io/docplex-doc/)
- [GradientDescent](https://qiskit.org/documentation/stubs/qiskit.algorithms.optimizers.GradientDescent.html)
- [Qiskit Gradient Framework](https://qiskit.org/documentation/tutorials/operators/02_gradients_framework.html)
- [梯度计算效率比较](https://tensorcircuit.readthedocs.io/zh/stable/tutorials/gradient_benchmark_cn.html)
- [梯度和变分优化](https://tensorcircuit.readthedocs.io/zh/stable/tutorials/gradient_benchmark_cn.html)

### 拓展

> 难点：论文阅读、算法细节
>
> 难度：高级

#### 任务拓展

在任务中，我们只能用0或1确定买或不买，该怎么样确定每只股票购买多少份额呢？

参考资料：

- [Quantum computational finance: quantum algorithm for portfolio optimization](https://arxiv.org/abs/1811.03975)
- [Solving linear systems of equations using HHL and its Qiskit implementation](https://learn.qiskit.org/course/ch-applications/solving-linear-systems-of-equations-using-hhl-and-its-qiskit-implementation)

## 基本软件结构
``
C:.
│  浙江大学软件学院-量子金融组实验过程.md
│
└─summer-camp-2023
    │  .gitignore
    │  HHL_portfolio_optimization.ipynb: 关于HHL实现连续投资组合优化问题的代码
    │  Portfolio Optimization With Constraint.ipynb: 关于实现带约束投资组合问题的代码
    │  Portfolio Optimization With Unconstraint.ipynb: 关于实现不带约束的投资组合优化问题的代码
    │  README.md
    │
    └─test code: 一些实现过程中测试的遗留代码。
            example1.ipynb
            example2.ipynb
            HHL.ipyn
``

## 环境配置

创建虚拟环境，这里根据提供的建议，安装的Python版本为3.10。
```shell
conda create -n zju-summer-camp-qf-2023 python=3.10
conda activate zju-summer-camp-qf-2023
```

通过pip安装最新发行版本的Qiskit和Qiskit Finance（官网：https://qiskit.org/ecosystem/finance/）。
Qiskit Finance 是一个开源框架，其中包含股票/证券问题的不确定性组件、金融问题的应用程序（例如**投资组合优化**）以及用于获取真实或随机数据以资助实验的数据提供商。
```shell
python -m pip install qiskit

python -m pip install qiskit[finance]
```

安装相关可能使用到的画图工具：

```shell
pip install matplotlib
pip install pylatexenc
```

安装一些优化算法包：

```shell
python -m pip install scikit-opt == 0.6.5

```
由于最新版本的0.6.6的PSO不支持约束。

安装可用于`Jupyter`的`IPython`内核，即可在`VSCode`中运行`Jupyter Notebook`。

```shell
pip install ipykernel
```




