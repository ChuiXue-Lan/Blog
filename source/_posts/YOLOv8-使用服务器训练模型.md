---
title: YOLOv8 - 使用服务器训练模型
date: 2024-06-28T15:14:17+08:00
tags: YOLOv8
categories: Computer Vision
description: 使用恒源云服务器训练模型
series: YOLOv8
---
* 训练网站：
[恒源云_GPUSHARE-恒源智享云](https://www.gpushare.com/center/console)
* 用户文档：
[训练指引 - 恒源云用户文档](https://gpushare.com/docs/best_practices/train/)
[恒源云(GpuShare)_GPU租用保姆级教程，助力深度学习训练！_恒源云_InfoQ写作社区](https://xie.infoq.cn/article/32b709e6ac9ff73a2ca096a56)
* 常见问题：
[实例相关 - 恒源云用户文档](https://gpushare.com/docs/faq/instance/#sshssh)
* 使用流程：
![image.png](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291307357.png)
# 本地下载并安装 FileZilla
进入官网，按照下图顺序，下载FileZilla
![image.png](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291307301.png)
# 创建实例
创建实例后，如下图选择即可：![image.png](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291307261.png)
# 使用 FileZilla 上传数据
**1.打开FIleZilla图形化客户端** 双击打开FileZilla图形化客户端
**2.点击文件->站点管理器**[![](https://cdn.nlark.com/yuque/0/2024/png/22381734/1715501190619-027c091b-3e9d-4d65-890a-780f2e102c43.png#averageHue=%23efcf87&clientId=uf97204aa-848d-4&from=paste&id=ue8f43399&originHeight=1356&originWidth=2062&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=u6aa02434-0085-4cc9-83bb-afe1949404b&title=)](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291309171.png)
**3.点击新站点-选择SFTP协议**[![](https://cdn.nlark.com/yuque/0/2024/png/22381734/1715501190631-2c625339-73e9-4c4a-b144-d17864947ec5.png#averageHue=%23f0eeee&clientId=uf97204aa-848d-4&from=paste&id=u826559a9&originHeight=948&originWidth=1708&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=uc541d2c5-ec7a-448e-890f-c47fb76997e&title=)](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291309129.png)
**4.输入主机、端口、用户、密码** 登录类型选择：正常
>获取主机名、端口、用户名、密码
打开[恒源云控制台](https://gpushare.com/center/hire)，复制登录指令和密码（点击复制按钮），然后粘贴到文本或编辑器中。[![](https://cdn.nlark.com/yuque/0/2024/png/22381734/1715501442669-1c594928-bd90-434c-b14e-20d5611b75b5.png#averageHue=%23f7fdfc&clientId=uf97204aa-848d-4&from=paste&id=u6fe26c9f&originHeight=575&originWidth=2554&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=u4aad91c8-17e4-431f-9b91-6a8cfa52734&title=)](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291309955.png)
粘贴完成后如下所示：
>```
登录指令：ssh -p 6666 root@i-1.gpushare.com
密码：vKExWbBWnVkszkwaFdh4cPABADSNFGuS
>```
> 则命令拆解如下：
> * 实例SSH主机名：i-1.gpushare.com
> * 实例SSH端口号：6666
> * 实例用户名：root
> * 实例密码：vKExWbBWnVkszkwaFdh4cXXXXXXXXXXX

[![](https://cdn.nlark.com/yuque/0/2024/png/22381734/1715501190579-e4c51096-26df-401f-85d9-d5c7bf4e5a90.png#averageHue=%23efebea&clientId=uf97204aa-848d-4&from=paste&id=uecb3764a&originHeight=948&originWidth=1708&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=udfd0fa2a-0f73-45f7-a7c2-7ecbca3e7e3&title=)](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291309910.png)然后点击连接
**5.红色框中的目录是实例中的目录，绿色框中的目录为您电脑本地目录**
[![](https://cdn.nlark.com/yuque/0/2024/png/22381734/1715501190878-461c06e9-f37a-4f98-98d2-3d4ae7cf0bff.png#averageHue=%23f5f4f4&clientId=uf97204aa-848d-4&from=paste&id=u45d3fe87&originHeight=1880&originWidth=2934&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=u64b04fcc-1fb8-4099-86f2-dc2e21c6fb0&title=)](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291309864.png)
**6.进入实例中的/hy-tmp目录**
[![](https://cdn.nlark.com/yuque/0/2024/png/22381734/1715501190845-a8e41ba8-8c5b-4049-9f69-e2a6560cb6f5.png#averageHue=%23f7f6f6&clientId=uf97204aa-848d-4&from=paste&id=ubcfae80e&originHeight=1900&originWidth=2946&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=u1a4c5040-2a30-47ec-83de-8d2c58e9054&title=)](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291309808.png)
**7.将本地数据传输到实例中。**
**本地数据指包含数据集的 Ultralytics 的压缩包。**
[![](https://cdn.nlark.com/yuque/0/2024/png/22381734/1715501196264-80e2b611-d625-4742-a00c-7b4472c73303.png#averageHue=%23f8f7f6&clientId=uf97204aa-848d-4&from=paste&id=u5555449b&originHeight=1790&originWidth=2950&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=uc3217936-a82b-4bfa-9ad4-b4edea0476b&title=)](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291309755.png)
# 训练模型
当创建实例并启动后，可以在实例列表中点击链接打开 **JupyterLab**。
[![](https://cdn.nlark.com/yuque/0/2024/png/22381734/1715504117775-98e95600-9319-4772-9326-4430f02a4c0f.png#averageHue=%2382cc8f&clientId=ubc91e51b-a4af-4&from=paste&id=u56e560f8&originHeight=795&originWidth=1355&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=u1492bdc8-13a7-4046-9669-0ffeb06f344&title=)](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291309718.png)
打开后进入到启动页。左侧为文件浏览器，可以对实例内的所有文件。右侧为工作区域。
[![](https://cdn.nlark.com/yuque/0/2024/png/22381734/1715504117739-5a94cb99-cbdf-4d24-8f33-f2f31790fa44.png#averageHue=%23f7f7f7&clientId=ubc91e51b-a4af-4&from=paste&id=u9a6a5172&originHeight=795&originWidth=1355&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=u01dc9cf6-5203-4af2-a7de-775d0f1060c&title=)](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291316450.png)
默认提供的 **JupyterLab** 为中文汉化界面，可以在菜单 **设置** - **语言** 调整为英语界面。
![](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291316404.png)
## 运行终端
在启动页中点击 **其他** - **终端** 新建终端。或在菜单中 **文件** - **新建** - **终端** 创建终端。
![](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291316361.png)
![](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291316316.png)
打开终端页后可以直接执行命令。
![](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291316272.png)
使用完成后在终端内执行 logout 或 Ctrl + D 来正常退出终端。
如果直接关闭了终端的窗口，这个终端仍然会在后台继续运行，包括在正在执行的命令任务。想找回之前关闭的终端窗口，可以在左侧菜单栏点击 **正在运行终端和内核** 按钮，查看运行中的终端。
![](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291316217.png)
点击正在运行的终端可以重新打开这个终端的标签页。当显示空白可以输入 Enter 来打印一次终端提示符。
![](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291316169.png)
## 解压个人数据
先进入个人数据存放文件夹（hy-tmp）:`cd hy-tmp`
![image.png](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291316123.png)
然后解压：`unzip ultralytics-8.0.48.zip`
然后进入加压后文件夹：![image.png](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291321064.png)
## 部署环境
下载 ultralytics-xxx、requirements.txt
```
pip install ultralytics==8.0.48
pip install -r requirements.txt
```
>可能的报错 ①
报错信息：
`pip._vendor.urllib3.exceptions.ProtocolError: ("Connection broken: ConnectionResetError(104, 'Connection reset by peer')", ConnectionResetError(104, 'Connection reset by peer'))`
>
>解决方案：
重新创建示例，更换 pytorch 版本：1.13.1

>可能出现的报错 ②
报错信息：
`WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: [https://pip.pypa.io/warnings/venv](https://pip.pypa.io/warnings/venv)`
>
>解决方案：创建虚拟环境
`conda create -n myenv python=3.8`
`conda activate myenv`
然后再部署环境
## 命令行训练
在终端输入命令行进行训练
`yolo task=detect mode=train model=datasets/yolov8n.yaml data=datasets/data.yaml epochs=200 imgsz=640 resume=True`
>可能的报错报错信息：
`FileNotFoundError: `
`Dataset 'datasets/data.yaml' not found ⚠️, missing paths ['/hy-tmp/ultralytics-8.0.48/datasets/datasets/datasets/valid/images']`
>
>解决：
![image.png](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291316123.png)
# 下载结果
**1.通过FIleZilla客户端连接站点**
[![](https://cdn.nlark.com/yuque/0/2024/png/22381734/1715517903274-1ef68a2a-eeb9-4877-87e3-7b856eac253b.png#averageHue=%23efebea&clientId=u948cb39e-23f0-4&from=paste&id=u23a64e86&originHeight=948&originWidth=1708&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=ue22ce5c0-8008-4da4-a108-72cc1936ba3&title=)](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291316082.png)
**2.进入实例/hy-tmp/目录**
[![](https://cdn.nlark.com/yuque/0/2024/png/22381734/1715517903604-a07fa841-5452-4acf-83c5-1b2162b46208.png#averageHue=%23f6f6f5&clientId=u948cb39e-23f0-4&from=paste&id=u17bf58d8&originHeight=1910&originWidth=2940&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=uae0f288b-2b6c-48fe-8c25-1a043bab841&title=)](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291316037.png)
**3.将实例/hy-tmp/目录中的数据下载到本地电脑**
[![](https://cdn.nlark.com/yuque/0/2024/png/22381734/1715517903148-d192a59d-1eac-4be1-87cb-8f0d7b199021.png#averageHue=%23f9f8f7&clientId=u948cb39e-23f0-4&from=paste&id=u30934ff1&originHeight=1294&originWidth=2956&originalType=url&ratio=1.25&rotation=0&showTitle=false&status=done&style=none&taskId=u6c92e411-0833-4168-9e4a-b27c79b0ae5&title=)](https://raw.githubusercontent.com/ChuiXue-Lan/image-host/main/blog-image/202406291316994.png)

# 系列文章
{% series YOLOv8 %}