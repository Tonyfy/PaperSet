# PaperSet
关注的一些CV，ML方面的论文

## CNN 应用

* Joint Face Detection and Alignment using Multi-task Cascaded Convolutional Networks
使用多级级联CNN网络的思路解决人脸检测和人脸标定的任务。

第一级网络 P-NET 输入12x12x3 的彩色图块，第二级网络 R-NET 输入24x24x3 的彩色图块，第三级网络 O-NET 输入48x48x3 的彩色图块，各级网络都融合了分类loss和标定的回归loss。

该算法方案使用wider 数据库，在fddb上达到近95%的准确率。

 
