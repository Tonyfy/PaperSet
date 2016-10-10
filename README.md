# PaperSet
关注的一些CV，ML方面的论文

## CNN 应用

* [Joint Face Detection and Alignment using Multi-task Cascaded Convolutional Networks](https://arxiv.org/ftp/arxiv/papers/1604/1604.02878.pdf)
使用多级级联CNN网络的思路解决人脸检测和人脸标定的任务。

第一级网络 P-NET 输入12x12x3 的彩色图块，第二级网络 R-NET 输入24x24x3 的彩色图块，第三级网络 O-NET 输入48x48x3 的彩色图块，各级网络都融合了分类loss和标定的回归loss。

该算法方案使用wider 数据库，在fddb上达到近95%的准确率。


 * Accelerating Deep Convolutional Networks using low-precision and sparsity

 使用低精度和稀疏化实现深度卷积网络的加速，2bit的计算精度，在1Tflop设备上正常工作，效率提升较大。

* Rich feature hierarchies for accurate object detection and semantic segmentation

R-CNN，region of CNN feature。

1.首先基于原始图像生成种类独立的区域，这些区域构成了我们detector的候选检测集

2.对第一步提取的所有区域应用CNN结构，得到一个固定长度的特征向量

3.使用特定的SVM分类器对第二步的特征向量进行分类


* Spatial Pyramid Pooling in Deep Convolutional Networks for Visual Recognition

* Fast R-CNN

使用一个全连接层，取代SVM。增加分类和位置精修的双路输出。

