# PaperSet
paper set of computer vision，high-performance computing，Deep learning ，CNN，GAN，RNN，etc

## visualising
* [VisualBackProp: visualizing CNNs for autonomous driving](https://arxiv.org/pdf/1611.05418v2.pdf)

在CNN 网络的feature map 中显示输入的哪些像素对结果的响应最大，并在自动驾驶场景实验。

## Learning Strategy

* [Layer Normalization](https://arxiv.org/abs/1607.06450v1)

基于对 batch Normalization 优缺点的思考，本文提出了Layer Normalization的方法，下面是两者对比情况：

|optimization method|training time of DNN|On RNN|Train/Test Phase|
|-------------------|--------------------|------|----------------|
|Batch Normalization| accelerate the SGD |not directly use|only for Train|
|Layer Normalization| accelerate more    |both CNN,RNN|both for Train and Test|

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

* A Discriminative Feature Learning Approach for Deep Face Recognition

与传统人脸识别类的CNN网络模型相比，除了使用softmax 的分类loss之外（可体现类间的区别特性），增加了center loss用于增加类内的聚合特性。两个loss共同监督模型的训练，增加额外的参数进行loss权值的控制。

在小训练集的限制下，本文的改进可以达到更高的准确率。

* [Learning Deep Feature Representations with Domain Guided Dropout for Person Re-identification](https://arxiv.org/pdf/1604.07528v1.pdf)

CVPR2016 person Re-ID use multi datasets.

* [Joint Face Representation Adaptation and Clustering in Videos](http://personal.ie.cuhk.edu.hk/~ccloy/files/eccv_2016_joint.pdf)

ECCV 2016 吕健勤等

* [Accelerating the Super-Resolution Convolutional Neural Network](http://personal.ie.cuhk.edu.hk/~ccloy/files/eccv_2016_accelerating.pdf)

ECCV 2016 超分辨率 吕健勤
