# Human Body strcuture

## Detecting and Recognizing Human-Object Interactions
 
 数据对象：图像
 任务：检测和识别出图像中，以人物为中心的交互行为。
 概念：数据元（人，动词，其他交互物体）三元组。

### 创新

基于三元组数据，设计训练了InteractNet网络。模型结构为

![model][model-arch]

[model-arch]:imgs/model-arch.png

模型包含：目标物体检测，动作分类和交互检测（定位）三个方面。

交互检测需要从人物ROI中定位到交互行为发生的具体位置，如下图。

![interact-posi][i-p]

[i-p]:imgs/interact-position.png

本方案在V-COCO上的检测识别效果如下

![result][re]

[re]:imgs/result.png

### 数据集
V-COCO是依托[COCO数据集](../../../6-Data-Competetion/README.MD)组织出的用于检测识别人的交互动作的数据集，构建方式主要是使用COCO image caption的信息，提取出：

1，caption主语是人；
2，提取出包含一系列基础动词的；
3，交互较为丰富的图像。

组建而来。详见论文[Visual Semantic Role Labeling](./Visual Semantic Role Labeling 1505.04474.pdf)

coco的字幕标注：每张图片包含5个不同人物对图片内容的解读。

如，此处展示了使用python接口解析COCO中caption信息的[示例](https://github.com/pdollar/coco/blob/master/PythonAPI/pycocoDemo.ipynb)

![caption][v-cap]

[v-cap]:imgs/v-caption.png


## [Person Re-identification in the Wild](https://arxiv.org/abs/1604.02531v2)

1.提出新的数据集PRW
2.行人检测和特征提取
3.丰富的实验

## [Learning Deep Feature Representations with Domain Guided Dropout for Person Re-identification](https://arxiv.org/pdf/1604.07528v1.pdf)

CVPR2016 person Re-ID use multi datasets.
