## YOLOV4：You Only Look Once目标检测模型在Keras当中的实现
---

### 目录
1. [所需环境 Environment](#所需环境)
2. [文件下载 Download](#文件下载)
3. [训练步骤 How2train](#训练步骤)
4. [参考资料 Reference](#Reference)

### YOLOV4的改进
[x] 主干特征提取网络：DarkNet53 => CSPDarkNet53
[x] 特征金字塔：SPP，PAN
[x] 训练用到的小技巧：Mosaic数据增强、Label Smoothing平滑、CIOU、学习率余弦退火衰减
[x] 激活函数：使用Mish激活函数
[x] ……balabla

### 所需环境
tensorflow-gpu==1.13.1  
keras==2.1.5  

### 文件下载
训练所需的yolo_weights.h5可以在Release里面下载。  
https://github.com/bubbliiiing/yolo3-keras/releases  
也可以去百度网盘下载  
链接: https://pan.baidu.com/s/1izPebZ6PVU25q1we1UgSGQ 提取码: tbj3  

### 训练步骤
1、本文使用VOC格式进行训练。  
2、训练前将标签文件放在VOCdevkit文件夹下的VOC2007文件夹下的Annotation中。  
3、训练前将图片文件放在VOCdevkit文件夹下的VOC2007文件夹下的JPEGImages中。  
4、在训练前利用voc2yolo3.py文件生成对应的txt。  
5、再运行根目录下的voc_annotation.py，运行前需要将classes改成你自己的classes。  
```python
classes = ["aeroplane", "bicycle", "bird", "boat", "bottle", "bus", "car", "cat", "chair", "cow", "diningtable", "dog", "horse", "motorbike", "person", "pottedplant", "sheep", "sofa", "train", "tvmonitor"]
```
6、就会生成对应的2007_train.txt，每一行对应其图片位置及其真实框的位置。  
7、在训练前需要修改model_data里面的voc_classes.txt文件，需要将classes改成你自己的classes。  
8、运行train.py即可开始训练。  

### Reference
https://github.com/qqwweee/keras-yolo3/
