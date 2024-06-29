---
title: YOLOv8 - 自定义数据集并训练
date: 2024-06-28T14:25:06+08:00
tags: YOLOv8
categories: Computer Vision
cover: /img/cover1.jpg
description: 建立属于自己的数据集，并在其基础上进行训练
series: YOLOv8(3)
---
参考视频：<br />[【yolov8】从0开始搭建部署YOLOv8，环境安装+推理+自定义数据集搭建与训练，一小时掌握_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1fY411y7Xq/)
> 本文参考以上视频第5部分

# 基础
## 配置文件：default.yaml
YOLOv8持续更新，项目结构会有变化<br />快捷查找配置文件方式：`ctrl+shift+N`，然后选择所有或文件，之后输入default搜索即可<br />default.yaml中参数可以写在yolo CLI中
## 推理命令：
`yolo task=detect mode=predict model=yolov8n.pt conf=0.25 source='...'`<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/22381734/1704876275154-9230d794-87b1-403f-9af9-2cb2cd7c5859.png#averageHue=%232f2c2b&clientId=u191ae853-7414-4&from=paste&height=49&id=u15d08a90&originHeight=61&originWidth=832&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=15964&status=done&style=none&taskId=u16159061-9838-403d-94e0-98b8eb83ef1&title=&width=665.6)<br />task：任务<br />mode：模式<br />model：选择自己训练的模型或官方模型<br />conf：置信度<br />source：图片/视频路径
# 数据集的结构与制作
## datasets文件结构
![image.png](https://cdn.nlark.com/yuque/0/2024/png/22381734/1704877769520-513622de-f4b3-4eba-9042-4cf42766bebd.png#averageHue=%23f3f0ea&clientId=u1d43b295-eeb4-4&from=paste&height=104&id=uc8c2045d&originHeight=130&originWidth=164&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=2744&status=done&style=none&taskId=u4917e404-7a65-4a06-b041-63362851f23&title=&width=131.2)![image.png](https://cdn.nlark.com/yuque/0/2024/png/22381734/1704877729574-8f44aa00-3cc8-4bf1-abfc-fbe7d409b723.png#averageHue=%23f3f0e8&clientId=u1d43b295-eeb4-4&from=paste&height=46&id=UZupN&originHeight=58&originWidth=158&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=1549&status=done&style=none&taskId=uff827d36-79ba-440d-835b-273858a7716&title=&width=126.4)

> 数据结构
datasets
│
├─ test
│ ├─ images
│ │ └─ ······
│ └─ labels
│ └─ ······
│
├─ train
│ ├─ images
│ │ └─ ······
│ └─ labels
│ └─ ······
│
├─ valid
│ ├─ images
│ │ └─ ······
│ └─ labels
│ └─ ······
│
├─ data.yaml
└─ yolov8n.yaml

yolov8.yaml：从官网拉取下来的yolov8项目中包含，复制到datasets文件夹下面即可。<br />data.yaml内容：
```yaml
train: ../datasets/train/images # 此处建议写绝对路径
val: ../datasets/valid/images
test: ../datasets/test/images

nc: 2 # 该数据集中类的个数，一定写对，否则报错
# Classes
names:
  0: person # 每个类对应的名称
  1: bicycle
```
## 标注格式转换
> yolov8只支持txt类型标注！！见官网原文

参考文档：<br />[目标检测，将xml格式的标签数据集转换为yolov8(txt)格式_xwyd转yolo格式-CSDN博客](https://blog.csdn.net/fisheryjn/article/details/133884219)
```python
import os
from lxml import etree

source_path = 'D:/source/label/path/'
label_path = 'D:/new/label/path'
 
#创建txt标签存放路径
if not os.path.exists(label_path):
    os.mkdir(label_path)
 
#获取文件名称列表
files = os.listdir(source_path)

#获取分类名称列表
def get_classes(files,source_path):
    class_set = set([])
    for file in files:
        with open(source_path+file,'rb') as fb:
            #解析xml文件
            xml = etree.HTML(fb.read())
            labels = xml.xpath('//object')
            for label in labels:
                name = label.xpath('./name/text()')[0] 
                class_set.add(name)
    return list(class_set)
 
classes = get_classes(files,source_path)
 
#生成分类字典，列如{'apple':0,'banana':1}
class_dict = dict(zip(classes,range(len(classes))))

def convert_xml2txt(file_name,source_path,label_path,class_dict,norm=False):
    #创建txt文件，并打开、写入
    new_name = file_name.split('.')[0] + '.txt'
    f = open(label_path+'/'+new_name,'w')
    with open(source_path+file_name,'rb') as fb:
        #开始解析xml文件，获取图像尺寸
        xml = etree.HTML(fb.read())
        width = int(xml.xpath('//size/width/text()')[0])
        height = int(xml.xpath('//size/height/text()')[0])
        #获取对象标签
        labels = xml.xpath('//object') #单张图片中的目标数量 len(labels)
        for label in labels:
            name = label.xpath('./name/text()')[0]         
            label_class = class_dict[name]
            xmin = int(label.xpath('./bndbox/xmin/text()')[0])
            xmax = int(label.xpath('./bndbox/xmax/text()')[0])
            ymin = int(label.xpath('./bndbox/ymin/text()')[0])
            ymax = int(label.xpath('./bndbox/ymax/text()')[0])
 
            #xyxy-->xywh,且归一化
            if norm :
                dw = 1 / width
                dh = 1 / height
                x_center = (xmin + xmax) / 2
                y_center = (ymax + ymin) / 2
                w = (xmax - xmin)
                h = (ymax - ymin)
                x, y, w, h = x_center * dw, y_center * dh, w * dw, h * dh
                f.write(str(label_class)+' '+str(x)+' '+str(y)+' '+str(w)+' '+str(h)+' '+'\n')
    #关闭文件
    f.close()
 
for file in files:
    convert_xml2txt(file,source_path,label_path,class_dict,norm=True)
```
## 将数据集划分为test，train，valid
```python
import os
import random
from tqdm import tqdm

# 指定 images 文件夹路径
image_dir = "D:/datasets/coco128/images"
# 指定 labels 文件夹路径
label_dir = "D:/datasets/coco128/labels"
# 创建一个空列表来存储有效图片的路径
valid_images = []
# 创建一个空列表来存储有效 label 的路径
valid_labels = []

# 遍历 images 文件夹下的所有图片
for image_name in os.listdir(image_dir):

    # 获取图片的完整路径
    image_path = os.path.join(image_dir, image_name)
    # 获取图片文件的扩展名
    ext = os.path.splitext(image_name)[-1]
    # 根据扩展名替换成对应的 label 文件名
    label_name = image_name.replace(ext, ".txt")
    # 获取对应 label 的完整路径
    label_path = os.path.join(label_dir, label_name)

    # 判断 label 是否存在
    if not os.path.exists(label_path):
        # 删除图片
        # os.remove(image_path)
        # print("deleted:", image_path)
        print("delete")
    else:
        # 将图片路径添加到列表中
        valid_images.append(image_path)
        # 将label路径添加到列表中
        valid_labels.append(label_path)
        # print("valid:", image_path, label_path)

# 遍历每个有效图片路径

for i in tqdm(range(len(valid_images))):
    image_path = valid_images[i]
    label_path = valid_labels[i]

    # 随机生成一个概率
    r = random.random()

    # 判断图片应该移动到哪个文件夹
    # train：valid：test = 7:2:1
    if r < 0.1:
        # 移动到 test 文件夹
        destination = "D:/Pycharm/ultralytics-main/datasets/test"
    elif r < 0.2:
        # 移动到 valid 文件夹
        destination = "D:/Pycharm/ultralytics-main/datasets/valid"
    else:
        # 移动到 train 文件夹
        destination = "D:/Pycharm/ultralytics-main/datasets/train"

    # 生成目标文件夹中图片的新路径
    image_destination_path = os.path.join(destination, "images", os.path.basename(image_path))
    # 移动图片到目标文件夹
    os.rename(image_path, image_destination_path)
    # 生成目标文件夹中 label 的新路径
    label_destination_path = os.path.join(destination, "labels", os.path.basename(label_path))
    # 移动 label 到目标文件夹
    os.rename(label_path, label_destination_path)

print("valid images:", valid_images)

# 输出有效label路径列表
print("valid labels:", valid_labels)
```
> 注1：想使用以上划分代码，则必须严格遵守本文datasets文件结构
> 注2：填写正确的数据集路径，如images文件夹下可能还有子文件夹而非直接是图片文件，labels同理

# 用自定义数据集训练
## 训练模型

1. 开始训练：

    `yolo task=detect mode=train model=datasets/yolov8n.yaml data=datasets/data.yaml epochs=10000 imgsz=640 resume=True workers=2 batch=16 amp=False`
    `yolo task=detect mode=train model=datasets/yolov8n.yaml data=datasets/data.yaml epochs=500 imgsz=640 resume=True workers=2 batch=16 amp=False`

> 可能出现的问题 ①
终端中可能显示正在等待下载Arial.ttf，则点击其后的网站下载该文件即可。

> 可能出现的问题 ②
`WARNING No labels found in D:\Pycharm\ultralytics-main\datasets\train\labels.cache, training may not work correctly.`<br />查看数据集标注是否为txt类型。

> 可能出现的问题 ③
`WARNING No labels found in D:\Pycharm\ultralytics-main\datasets\train\labels.cache, training may not work correctly.`

> 可能出现的问题 ④
训练过程中数值出现nan：<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/22381734/1705821637154-2be11aec-4903-4074-9a07-6802c7d706a0.png#averageHue=%232f2e2d&clientId=ub7ef32d3-46ee-4&from=paste&height=194&id=ufb74a71f&originHeight=243&originWidth=1398&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=36247&status=done&style=none&taskId=u18b12bd2-20b8-4da4-8e7a-7defa5767a0&title=&width=1118.4)<br />这是有问题的，正常应该是一个数值:<br />![image.png](https://cdn.nlark.com/yuque/0/2024/png/22381734/1705826214156-b1562edb-69fd-4e38-b4be-9a9b7dcf7014.png#averageHue=%2331302f&clientId=u0634e01f-0f1e-4&from=paste&height=306&id=u417f7cf8&originHeight=383&originWidth=1383&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=71044&status=done&style=none&taskId=uee45b7f4-73d3-408e-97e0-02b7b7e3706&title=&width=1106.4)<br />解决方案：
① 设置batch，慢慢试，一般缩小，我使用16可以正常训练<br />② 设置`amp=false`<br />参考文档：<br />[yolov5和yolov8在train时，出现box_loss、cls_loss、dfl_loss为nan，Box(P R mAP50 mAP50-95)为0的解决办法-CSDN博客](https://blog.csdn.net/weixin_42283539/article/details/129988766)

2. 中断训练：按下Ctrl+C键来手动停止训练
3. 中断续训：

    将来自内容根的路径填入model中（注：填写last.pt的路径）
    `yolo task=detect mode=train model=runs/detect/train/weights/last.pt epochs=500 imgsz=640 resume=True workers=2`
    `yolo task=detect mode=val model=runs/detect/train/weights/last.pt<br />yolo detect val model=./runs/detect/train/weights/best.pt`

![获取来自内容根的路径](https://cdn.nlark.com/yuque/0/2024/png/22381734/1704883510382-6c6520e0-6f25-499f-b6a2-ef94afd82ca7.png#averageHue=%233c4145&clientId=u1d43b295-eeb4-4&from=paste&height=229&id=u8059fe5c&originHeight=286&originWidth=726&originalType=binary&ratio=1.25&rotation=0&showTitle=true&size=32096&status=done&style=none&taskId=u23298acd-823b-43af-ba71-ccf3325f9aa&title=%E8%8E%B7%E5%8F%96%E6%9D%A5%E8%87%AA%E5%86%85%E5%AE%B9%E6%A0%B9%E7%9A%84%E8%B7%AF%E5%BE%84&width=580.8 "获取来自内容根的路径")
## 利用模型推理
填写best.pt的路径到model中
`yolo task=detect mode=predict model=runs/detect/train/weights/best.pt conf=0.25 source='ultralytics/assets/bus.jpg'`
整体推理：
`yolo task=detect mode=predict model=runs/detect/train/weights/best.pt conf=0.25 source='datasets/test/images'`

> 关于 ultralytics 8.0.48
对于ultralytics 8.0.48 需要找到yolov8n.yaml，不能像8.1.X版本，用yolov8.yaml
并且`yolo detect train model=datasets/yolov8n.yaml data=datasets/data.yaml epochs=500 imgsz=640 resume=True batch=16`
`yolo task=detect mode=train model=datasets/yolov8n.yaml data=datasets/data.yaml epochs=500 imgsz=640 resume=True batch=2 workers=2`
[KeyError: ‘depth_multiple’ · Issue #1 · OutBreak-hui/YoloV5-Flexible-and-Inference](https://github.com/OutBreak-hui/YoloV5-Flexible-and-Inference/issues/1)
![image.png](https://cdn.nlark.com/yuque/0/2024/png/22381734/1706325825017-1d15670a-1598-46db-9f07-8a13fc96677f.png#averageHue=%23272b2c&clientId=u6e79ff92-055a-4&from=paste&height=361&id=ubae11906&originHeight=451&originWidth=1142&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=55033&status=done&style=none&taskId=u57e63f15-cbe0-401f-ad06-2fdd70f59b5&title=&width=913.6)
一个重点报错！！使用以下命令行`yolo detect train model=datasets/yolov8n.yaml data=datasets/data.yaml epochs=500 imgsz=640 resume=True batch=16`
如果路径正确，却还报错路径找不到，说明 data.yaml 中没有使用绝对路径；或 yolo.yaml 文件 nc 没有写对；或文件命名有问题如 valid 写为 vaid







<!-- {% tabs 关于 ultralytics 8.0.48 %}
<!-- tab -->

对于ultralytics 8.0.48 需要找到yolov8n.yaml，不能像8.1.X版本，用yolov8.yaml
并且`yolo detect train model=datasets/yolov8n.yaml data=datasets/data.yaml epochs=500 imgsz=640 resume=True batch=16`
`yolo task=detect mode=train model=datasets/yolov8n.yaml data=datasets/data.yaml epochs=500 imgsz=640 resume=True batch=2 workers=2`
[KeyError: ‘depth_multiple’ · Issue #1 · OutBreak-hui/YoloV5-Flexible-and-Inference](https://github.com/OutBreak-hui/YoloV5-Flexible-and-Inference/issues/1)
![image.png](https://cdn.nlark.com/yuque/0/2024/png/22381734/1706325825017-1d15670a-1598-46db-9f07-8a13fc96677f.png#averageHue=%23272b2c&clientId=u6e79ff92-055a-4&from=paste&height=361&id=ubae11906&originHeight=451&originWidth=1142&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=55033&status=done&style=none&taskId=u57e63f15-cbe0-401f-ad06-2fdd70f59b5&title=&width=913.6)
一个重点报错！！使用以下命令行`yolo detect train model=datasets/yolov8n.yaml data=datasets/data.yaml epochs=500 imgsz=640 resume=True batch=16`
如果路径正确，却还报错路径找不到，说明 data.yaml 中没有使用绝对路径；或 yolo.yaml 文件 nc 没有写对；或文件命名有问题如 valid 写为 vaid
<!-- endtab -->
{% endtabs %} -->
