# Object Detection

* Rich feature hierarchies for accurate object detection and semantic segmentation

R-CNN，region of CNN feature。

1.首先基于原始图像生成种类独立的区域，这些区域构成了我们detector的候选检测集

2.对第一步提取的所有区域应用CNN结构，得到一个固定长度的特征向量

3.使用特定的SVM分类器对第二步的特征向量进行分类
