# image segmentation

## Mask R-CNN
* FAIR hekaiming
* insight：在RCNN结构中，Boundding Box上加入一个小的FCN结构进行实例分割的任务。

提出了一种简洁灵活通用的目标分割框架Mask R-CNN。可以检测并同时获取各个目标的分割边界，相比于Faster R-CNN目标检测框架，仅仅增加了少量的耗时。可以在目标分割，物体边界检测和人体关键点检测上较好地使用。在COCO2016上表现很好。

### 框架
Mask R-CNN的结构如下

![mrcnn][mrcnn]

[mrcnn]:imgs/Mask-R-CNN.png

### noval

* 多任务训练：Lclass+Lbounddingbox+Lmask

其中Lmask 仅由对应的class来贡献，其他类别对mask误差无贡献，将classification和mask解耦，mask的学习无需考虑各个类别之间的竞争，是一个新意。

对每个ROI，使用FCN预测一个mxm的Mask,与其他保留fc特征进行mask预测的方法相比，全卷积能适应各种尺寸，实验证明也更高效。

### ROIPool  -->ROIAlign
[9]提出的ROIPool从每一个ROI中提取一个小的特征图（如7x7）,在对ROI进行量化阶段，会导致ROI和提取的特征图之间失配。这对像素级的mask任务会带来较大影响。

因此提出ROIAlign层，去除了RoIPool中苛刻的量化操作，将ROI中提取的特征与输入图像进行了Aligning(对齐，匹配)：避免了对ROI边框或者二值进行任何量化，对每一个ROI bin,使用```双线性插值```计算输入特征的准确值。

RoiAlign 提升明显，对比ROIWarp..

### 实现

* 训练

![tra][tra]

[tra]:imgs/mrcnn-train.png

* 实验

![exp][exp]

[exp]:imgs/mrcnn-experiment.png

## Mixed context networks for semantic segmentation

* HIK. 2017

semantic segmentation 是比较难的问题，要确定图像中含有哪些物体，以及各个像素属于哪个物体。目前FCN 在这个问题上取得了相对较好的表现。而本文就如何利用不同层之间特征的关联，进行了设计和实验。提出的多语境混合的结构（MCN）表现较好，在PASCAL VOC 2012和MIT SceneParsing150上表现较好。

![arch][arch]

[arch]: imgs/mixed-context-networks.png