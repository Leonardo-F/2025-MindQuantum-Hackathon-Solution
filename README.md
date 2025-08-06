# 2025 MindSpore 量子计算黑客松 - 量子误差缓解赛道

本项目展示了高荣浩团队在量子误差缓解赛道的解决方案。项目针对量子计算中的测量误差问题，提出了基于单比特校准矩阵与局部 IBU (Iterative Bayesian Unfolding) 的测量误差校准方案。

- 赛事网址：https://developer.huaweicloud.com/competition/information/1300000041/html10

- 赛事代码仓：https://gitee.com/mindspore/mindquantum/pulls/2769

## 项目内容

- **赛题介绍**：[量子测量误差缓解](docs/赛题说明.md)
- **解决方案论文**：[基于单比特校准矩阵与局部 IBU 的测量误差校准方案](docs/readout-高荣浩.md)

## 联系方式

如有任何问题，欢迎通过以下邮箱联系项目团队：
`f.g.m.leonardo@gmail.com`


## 环境准备

本项目基于以下环境构建：
- Python 版本：`3.9.21`
- 主要依赖库：`mindquantum=0.10.0`

安装所需依赖：
```bash
pip install -r requirements.txt
```


## 项目结构说明

`docs` 中主要是赛题说明和论文 `markdown` 文件；

`code` 中除了代码文件 `.py` 外，还有需要校准的测量数据 `sample`：

- `answer.py`：是方案的可运行代码，包含原始ibu，向量化ibu，单比特局部ibu，矩阵求逆法，按需注释即可使用；

- `answer_test.py`：是测试代码，用来输出各基态在矩阵取逆法和局部 IBU 法下的性能对比，`Figure_1.png`是其输出的散点图；

- `answer_matrix.py`：是随机矩阵法，通过构造训练集，去训练校准矩阵，可直接运行，不需要通过 `run.py`。有两个可变的方法参数，`method="random_martix"`， `data_method="ground_state"`，表示初始化随机矩阵和使用基态构造的数据，可根据注释选择需要的方法。训练好的矩阵会进行存储；

- `matrix_picture.py`：是将训练好的矩阵，用于校准基态，查看其性能；

上述结果都放在 `result` 文件夹下
