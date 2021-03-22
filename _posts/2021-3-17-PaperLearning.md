---
layout:     post
title:      PaperLearning
subtitle:   PySlowFast
date:       2021-03-14
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - Paper 
   - Daily

---

# PySlowFast 论文复现

## 使用工具：CoLab

https://github.com/facebookresearch/SlowFast

参考 install.md 开始搭建环境。

https://github.com/facebookresearch/SlowFast/blob/master/INSTALL.md

## Installation

```python
!pip install 'git+https://github.com/facebookresearch/fvcore'
!pip install simplejson
!pip install av 
```

**ffmpeg需要安装4.0版本**

```python
!add-apt-repository ppa:jonathonf/ffmpeg-4
!apt install ffmpeg
!ffmpeg -version
```

```python
!pip install -U iopath
!pip install psutil
!pip install tensorboard
!pip install moviepy
```

**torch和torchvision的版本，由于Detectron2有要求，目前需要的版本是1.6以上。**

```python
!pip install -U torch==1.6.0 torchvision==0.7.0 cython
```

```python
!pip install -U 'git+https://github.com/facebookresearch/fvcore.git' 'git+https://github.com/cocodataset/cocoapi.git#subdirectory=PythonAPI'
!git clone https://github.com/facebookresearch/detectron2 detectron2_repo
!pip install -e detectron2_repo
```

**Pytorch**

```python
!git clone --recursive https://github.com/pytorch/pytorch
```

**PySlowFast**

```python
!git clone https://github.com/facebookresearch/slowfast
%cd /content/slowfast
!python setup.py build develop
```

```python
!wget https://dl.fbaipublicfiles.com/pyslowfast/model_zoo/ava/SLOWFAST_32x2_R101_50_50.pkl
```

## Do it

https://github.com/facebookresearch/SlowFast/blob/master/VISUALIZATION_TOOLS.md

### 构建ava.json

https://dl.fbaipublicfiles.com/pyslowfast/dataset/class_names/ava_classids.json

### 修改yaml文件

文件路径：slowfast/demo/AVA SLOWFAST_32x2_R101_50_50.yaml

```yaml
TRAIN:
  ENABLE: False
  DATASET: ava
  BATCH_SIZE: 16
  EVAL_PERIOD: 1
  CHECKPOINT_PERIOD: 1
  AUTO_RESUME: True
  CHECKPOINT_FILE_PATH: "" #与训练权重文件路径
  CHECKPOINT_TYPE: pytorch
#TENSORBOARD:
#  MODEL_VIS:
#    TOPK: 2
DEMO:
  ENABLE: True
  LABEL_FILE_PATH: "/slowfast/demo/AVA/ava.json"
  INPUT_VIDEO: "/2.mp4"  #输入视频文件
  OUTPUT_FILE: "/1.mp4"  #输出视频文件路径

  DETECTRON2_CFG: "COCO-Detection/faster_rcnn_R_50_FPN_3x.yaml"
  DETECTRON2_WEIGHTS: detectron2://COCO-Detection/faster_rcnn_R_50_FPN_3x/137849458/model_final_280758.pkl
```

### 运行

```python
!python tools/run_net.py --cfg demo/AVA/SLOWFAST_32x2_R101_50_50.yaml
```

