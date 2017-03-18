# Optimization

Papers introduce Optimization method in ML&DL.

* [Layer Normalization](https://arxiv.org/abs/1607.06450v1)

基于对 batch Normalization 优缺点的思考，本文提出了Layer Normalization的方法，下面是两者对比情况：

|optimization method|training time of DNN|On RNN|Train/Test Phase|
|-------------------|--------------------|------|----------------|
|Batch Normalization| accelerate the SGD |not directly use|only for Train|
|Layer Normalization| accelerate more    |both CNN,RNN|both for Train and Test|

* Learning from Imbalance Data



