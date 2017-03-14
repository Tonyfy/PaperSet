# image segmentation(图像分割/语义分割) 

## Mixed context networks for semantic segmentation

* HIK. 2017

semantic segmentation 是比较难的问题，要确定图像中含有哪些物体，以及各个像素属于哪个物体。目前FCN 在这个问题上取得了相对较好的表现。而本文就如何利用不同层之间特征的关联，进行了设计和实验。提出的多语境混合的结构（MCN）表现较好，在PASCAL VOC 2012和MIT SceneParsing150上表现较好。

![arch][arch]

[arch]:imgs/mixed context networks.png