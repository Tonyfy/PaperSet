# Object Detection

## OverFeat(Integrated Recognition,Localization and Detection using Convolutional Networks)

提出一种CNN框架，同时进行图像分类，检测和定位的任务。


## [R-CNN] Rich feature hierarchies for accurate object detection and semantic segmentation

``Regions with CNN features``

RCNN的整体框架分为3步：

![frame][rcnnframe]

[rcnnframe]:imgs/rcnn-frame.png



* 1.首先基于原始图像生成种类独立的区域，这些区域构成了我们detector的候选检测集(约2000个)
* 2.对第一步提取的所有区域，使用CNN提取特征。
* 3.使用线性SVM分类器对上述特征进行分类（k个二分类问题，k是类别总数）

## SPP (Spatial Pyramid Pooling in Deep Convolutional Networks for Visual Recognition)

传统的CNN网络结构中主要包含卷积层和全连接层，其中卷积层不限制输入图像的尺寸，但全连接层由于神经元数量是固定的，也即需要固定尺寸的输入数据。而SPP（Spatial pymaid Pooling,空间金字塔）在卷积层和全卷积层之间进行适配，保证任意尺寸的卷积结构均得到固定尺寸的特征输出，以供全连接层连接。如下图所示。

![spp-frame][sppframe]

[sppframe]:imgs/sppNet.png

具体的，SPP层的计算如下图所示，在最后一个卷积层输出的特征图基础上，进行三个尺度的Pooling采样，Pooling 采样的窗口大小则与特征图的尺寸成比例，使得采样后的尺寸固定，固定的特征输出尺寸为：（16+4+1）*k维。其中k(256)是最后一个卷积层卷积核的数量。

![sppunit][sppunit]

[sppunit]:imgs/spp-unit.png


## [fast RCNN]

与RCNN的区别：

* RCNN在训练阶段是分多级训练的，先训练region proposal的网络，再进行SVM分类器的训练，最后再学习bbox的回归器；
* RCNN在SVM和bbox回归器学习时，要提取每一张图像的每一个目标的proposal的特征，并写入磁盘。时间和空间复杂度都很大。
* 测试阶段，要对每个目标的proposal进行特征提取，非常耗时。

SPPNet即是针对RCNN的耗时问题，提出能够共享计算的结构，影响重大。而SPP同样具有多级训练的结构，不能发挥神经网络end2end结构的优势。

Fast RCNN的主要突破：

* 检测精度(mAP)上远高于RCNN
* 采用单级训练结构（end2end），多任务学习（Multi-task）
* 训练时能更新整个网络
* 不需要硬盘存储特征。

Fast RCNN结构如下，：

![frcnn-frame][frcnn-frame]

[frcnn-frame]:imgs/fRCNN-frame.png

使用全卷积网络提取特征图，使用ROI pooling 层接收任意尺寸的输入数据，得到固定尺寸的特征，并连接全连接层。ROI pooling层相比于SPP层，有一个小的改动，对卷积输出的特征图的每一个通道独立得进行pooling,而SPP是不区分不同卷积输出通道，整体进行pooling.(max pooling)

### 训练

多任务的误差函数为：

![frcnn-loss][frcnn-loss]

[frcnn-loss]:imgs/frcnn-loss.png

分类误差采用log loss,bbox的回归误差采用平滑的L1 loss,且区别背景（无groundtruth bbox）。

![frcnn-smoothl1][frcnn-smoothliloss]

[frcnn-smoothliloss]:imgs/frcnn-smooth_l1loss.png

相比SPPNET使用L2误差刻画bbox的回归误差，这种方式不易出现梯度爆炸，调参容易。


## [faster RCNN]
在SPP和Fast RCNN探路的基础上，继续提出了faster RCNN,沿用end2end结构，引入RPN结构（Region proposal Network）用全卷积网络预测目标的位置，以及目标分类的分数。该结构能够输出高质量的region(约300个，远小于SPP和fast RCNN的2000个)，同时将后续检测分类网络设计成共享RPN的卷积特征的结构，大幅降低运行耗时。

RPN可以理解为 ``attention机制``，即告诉后续网络往哪里看。

### anchor 

在解决目标多尺寸问题上，faster rcnn采用了anchor的结构设计，在每一个滑窗位置选用多尺度多比例的采样，耗时更少，适应性更强（将滑窗的步长，可设置较大）。

![fr-rcnn-mscale][fr-rcnn-mscale]

[fr-rcnn-mscale]:imgs/fr-rcnn-mscale.png

### RPN注意力机制

RPN的结构如下图所示,针对每个anchor box，均得到分类分数和回归位置，anchor的结构设计使得后续的检测方法能够应对各种尺寸和目标比例。：

![rpn][rpn-frame]

[rpn-frame]:imgs/rpn-frame.png

### faster RCNN 流程

流程图为：

![fr-rcnn][fr-rcnn]

[fr-rcnn]:imgs/fr-rcnn-frame.png

