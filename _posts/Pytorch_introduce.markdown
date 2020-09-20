---
layout:     post
title:      "[目标检测]：R-CNN入门"
subtitle:   " 目标检测开篇论文简单理解 "
date:       2020-09-20 
author:     "辛志超同学"
header-img: "img/post-bg-digital-native.jpg"
catalog: true
tags:
    - 目标检测

---

> 那是一种与生俱来的天赋，就好像矮人天生擅长舞锤，而精灵则拥有魔法庇护。那些数字时代的原住民们，天生具备着一种操纵数字世界的领悟。

## 目标检测基础

不同于分类问题，物体检测可能会存在多个检测目标，这不仅需要我们判别出各个物体的类别，而且还要准确定位出物体的位置

下面图片上有猫，有狗，还有小黄鸭，这是多物体检测:
![Detection](img/img/detection/rcnn/detectionjc.jpg "R-CNN")


## Bounding Box(bbox)
bbox是包含物体的最小矩形，该物体应在最小矩形内部，如上图红色框蓝色框和绿色框。

物体检测中关于物体位置的信息输出是一组(x,y,w,h)数据，其中x,y代表着bbox的左上角(或者其他固定点，可自定义)，对应的w,h表示bbox的宽和高.一组(x,y,w,h)可以唯一的确定一个定位框。

## Intersection over Union(IoU)
对于两个区域R和R′,则两个区域的重叠程度overlap计算如下:

O(R,R′)=|R∩R′|/|R∪R′|

在训练网络的时候，我们常依据侯选区域和标定区域的IoU值来确定正负样本。
![Detection](img/img/detection/rcnn/iou.png "IOU")



## 非极大值抑制(Non-Maximum Suppression又称NMS)
非极大值抑制(NMS)可以看做是局部最大值的搜索问题，NMS是许多计算机视觉算法的部分。如何设计高效的NMS算法对许多应用是十分关键的，例如视频跟踪、数据挖掘、3D重建、物体识别以及纹理分析等。

针对非极大值抑制在物体检测上的应用，非极大值抑制就是把不是极大值的抑制掉，在物体检测上，就是对一个目标有多个标定框，使用极大值抑制算法滤掉多余的标定框。

下图一个小猫有多个红框标定：
![Before](img/img/detection/rcnn/beforenms.png "NMS")
![After](img/img/detection/rcnn/afternms.png "NMS")

## RCNN论文
如上图所示，R-CNN这个物体检查系统可以大致分为四步进行：

1.获取输入图像

2.提取约2000个候选区域(Region proposals)

3.将候选区域分别输入CNN网络（这里需要将候选图片进行缩放）

4.将CNN的输出输入SVM中进行类别的判定

上述四个步骤是一个大致的过程，而且是一个检测的过程，实际上训练过程比较麻烦。


<pre>
    Icon
主屏幕 ⇌ 应用
    Home 
</pre>



