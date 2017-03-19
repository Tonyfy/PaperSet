# Face Recognition

compare of difference methods.
|method|train data|performance on LFW|fps|model size|
|------|----------|------------------|----|---------|
|DeepFace|private|97.35%|--|--|
|Lightended CNN|CASIA|98.8%|16|28MB|

* A Discriminative Feature Learning Approach for Deep Face Recognition

与传统人脸识别类的CNN网络模型相比，除了使用softmax 的分类loss之外（可体现类间的区别特性），增加了center loss用于增加类内的聚合特性。两个loss共同监督模型的训练，增加额外的参数进行loss权值的控制。

在小训练集的限制下，本文的改进可以达到更高的准确率。

* [Learning Deep Feature Representations with Domain Guided Dropout for Person Re-identification](https://arxiv.org/pdf/1604.07528v1.pdf)

CVPR2016 person Re-ID use multi datasets.

* [Joint Face Representation Adaptation and Clustering in Videos](http://personal.ie.cuhk.edu.hk/~ccloy/files/eccv_2016_joint.pdf)


