---
title: YOLOv8 - 环境配置
date: 2024-06-28T13:25:53+08:00
tags: YOLOv8
categories: Computer Vision
cover: /img/background2.jpg
description: 在PyTorch虚拟环境中配置YOLOv8，进行每个步骤请仔细阅读本文档！
series: YOLOv8(1)
---
> 本文内容：在PyTorch虚拟环境中配置YOLOv8，进行每个步骤请仔细阅读本文档！

# Anaconda的安装
参考文档：
[Anaconda安装与Python环境搭建（不看后悔版）](https://zhuanlan.zhihu.com/p/511233749)
anaconda清华源安装：
[Index of /anaconda/archive/ | 清华大学开源软件镜像站 | Tsinghua Open Source Mirror](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)
> 注：本部分只安装 Anaconda

# PyTorch的配置准备
参考视频：
[【yolov8】从0开始搭建部署YOLOv8，环境安装+推理+自定义数据集搭建与训练，一小时掌握_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1fY411y7Xq/)
注：本视频参考到23min即可，后面up的配置有一些问题	
> 需要下载的内容
> ① 首先在官网`https://pytorch.org/`查看pytorch支持的最高版本  
> ② 不需要查看N卡系统支持最高的版本，下载CUDA版本会改变相关信息，此处不要被以上视频误导。
> ③ 权衡下载支持最高版本的CUDA和cuDNN（我下载的是CUDA_11.8，cuDNN下载11.）
> CUDA工具包：
> https://developer.nvidia.cn/zh-cn/cuda-toolkit
> CUDA_11.8下载网址:（若CUDA下载页面无法打开，可使用以下地址下载CUDA_11.8）[https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda_11.8.0_522.06_windows.exe](https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda_11.8.0_522.06_windows.exe)
> cuDNN：
> https://developer.nvidia.com/rdp/cudnn-download
> 注：最后是`cudnn-windows-x86_64-8.9.7.29_cuda11-archive`
> ④ 配置对应的环境变量
> nvcc -V：查看版本CUDA

# PyTorch的配置
## 参考文档：
[PyTorch 最新安装教程（2022-02-22）](https://zhuanlan.zhihu.com/p/470841101)<br />
注1：其中配置清华源会导致 Anaconda Prompt 报错
> 配置清华源报错解决方案将`C:/User/XXX/.condarc`中内容恢复为默认值:
> ```
> report_errors: false
> channels:
>   - defaults
> ```
> 或在 prompt 中运行：`conda config --remove-key channels`<br />然后在 Anaconda Prompt 中输入命令：`conda clean -i`<br />之后继续使用官网提供的命令下载 PyTorch 即可

> 可能可行的配置镜像源方案使用下文的方法三：可视化界面的方式配置镜像源
> [Anaconda配置镜像源_anaconda镜像源配置-CSDN博客](https://blog.csdn.net/qq_32650831/article/details/127952502)
> 若不可行，在 prompt 中运行：`conda config --remove-key channels`

注2：在使用官网提供的命令下载 PyTorch 中个别大文件下的较慢，请耐心等待。
注3：不要使用VPN。
注4：当下载完成后若 import torch 报错如下
```报错信息
ModuleNotFoundError: No module named ‘torch‘
```
则参考以下文档：
[ModuleNotFoundError: No module named ‘torch‘ 解决方案_modulenotfounderror: no module named ’torch-CSDN博客](https://blog.csdn.net/thy0000/article/details/122652349)
> 先下载numpy     conda install numpy
> 再重新输入官网提供的命令下载PyTorch（不需要删除）

## 下载/拉取ultralytics-main
[https://github.com/ultralytics/ultralytics](https://github.com/ultralytics/ultralytics)
release history：[https://pypi.org/project/ultralytics/#history](https://pypi.org/project/ultralytics/#history)
## 为 ultralytics-main 配置虚拟环境
将python项目解释器更换为刚刚创建好的虚拟环境
[在pycharm中设置Anaconda解释器_pycharm添加解释器anaconda-CSDN博客](https://blog.csdn.net/disccutter/article/details/124561073)
## 测试
```
import torch

print(torch.__version__)
print(torch.cuda.is_available())
print(torch.cuda.device_count())
print(torch.backends.cudnn.version())
print(torch.version.cuda)
quit()
```

![测试结果](https://github.com/ChuiXue-Lan/image-host/blob/main/blog-image/YOLOv8_1.1.png "测试结果")
# YOLOv8的配置
## 参考视频：
参考视频：参考以下视频第四部分
[【yolov8】从0开始搭建部署YOLOv8，环境安装+推理+自定义数据集搭建与训练，一小时掌握_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1fY411y7Xq)
在 Pycharm 终端中输入以下命令
```
pip install ultralytics -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install yolo -i https://pypi.tuna.tsinghua.edu.cn/simple
```
`pip install X库==版本号 -i https://pypi.tuna.tsinghua.edu.cn/simple`
## 配置测试
### 推理测试
```
//使用默认自带的一张图片进行测试
yolo task=detect mode=predict model=yolov8n.pt conf=0.25 source='ultralytics/assets/bus.jpg'
```
> yolov8n.pt 需要自己下载，并放置在根目录中！

> 报错信息：
> ```
> requests.exceptions.SSLError: HTTPSConnectionPool(host='api.github.com', port=443): Max retries exceeded with url: /repos/ultralytics/assets/releases/tags/v8.1.0 (Caused by SSLErro
> r(SSLZeroReturnError(6, 'TLS/SSL connection has been closed (EOF) (_ssl.c:1135)')))
> ```
> 解决方法：关闭 VPN 代理。
#### 问题解决
>可能出现的问题①
>若出现以下报错：
>`Error: No such command 'task=detect'.`
> 最新解决方案（成功！！！）：<br />卸载ultralytics再重新安装
> ```
> pip uninstall ultralytics
> pip install ultralytics -i https://pypi.tuna.tsinghua.edu.cn/simpl
> ```

> 解决方法（可能不成功）：<br />[yolov8训练自己的数据集，报错：no such command ‘detect‘或者command ‘yolo‘ not found_yolo: command not found-CSDN博客](https://blog.csdn.net/Jiangdan0326/article/details/129626121)
> 输入：python setup.py install 即可

> 若输入python setup.py install出现新报错：
> `can't open file 'setup.py': [Errno 2] No such file or directory`
> 解决方法：未知

> 可能出现的问题②
> 问题：在输入终端命令进行推理时一直显示链接github超时<br />原因：没有下载好模型<br />解决方案：可以先到github中下载对应模型（也可以在超时信息中直接找到对应下载网址），再放置在根文件夹下（注意不要放在子文件夹中！）
#### 测试结果
![推理测试成功结果](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/YOLOv8_1.2.png "推理测试成功结果")


