# yolo

### 1. Yolo 分类模型配置文件(model.yaml)

```yaml
# YOLOv11分类模型配置文件
model:
  # 输入通道数
  ch: 3
  # 分类数
  nc: 10
  # 模型结构
  backbone:
    - [Focus, [64, 3, 3], [32, 3, 1]]
    - [Conv, [64, 3, 2], [64, 3, 1]]
    - [C3, [64, 3, 1], [64, 3, 1]]
    - [Conv, [128, 3, 2], [64, 3, 1]]
    - [C3, [128, 3, 1], [128, 3, 1]]
    - [Conv, [256, 3, 2], [128, 3, 1]]
    - [C3, [256, 3, 1], [256, 3, 1]]
    - [Conv, [512, 3, 2], [256, 3, 1]]
    - [C3, [512, 3, 1], [512, 3, 1]]
    - [SPPF, [512, 5], [512, 3, 1]]
  head:
    - [Classify, [10], [512, 2, 1]]
```

### 2.数据集配置文件（data.yaml）

``` yaml
# 数据集配置文件
path: /path/to/dataset  # 数据集根目录
train: images/train  # 训练集图像文件夹
val: images/val  # 验证集图像文件夹

nc: 10  # 类别数
names: [class0, class1, class2, class3, class4, class5, class6, class7, class8, class9]  # 类别名称

```

### 3.训练参数配置文件（train.yaml）

```yaml
# 训练参数配置文件
train:
  imgsz: 224  # 输入图像大小
  batch: 16  # 批次大小
  epochs: 100  # 训练轮数
  workers: 8  # 数据加载线程数
  device: 0  # 训练设备（GPU编号）
  optimizer: Adam  # 优化器类型
  lr0: 0.001  # 初始学习率
  lrf: 0.1  # 最终学习率
  momentum: 0.937  # 动量
  weight_decay: 0.0005  # 权重衰减
  save_period: 10  # 每隔多少轮保存一次模型
  project: runs/train  # 保存模型的项目目录
  name: exp  # 保存模型的实验名称
  exist_ok: False  # 如果项目目录已存在，是否覆盖
  pretrained: True  # 是否使用预训练权重
  resume: False  # 是否从上次训练中断处继续训练

```

### 4.使用配置文件进行训练

```python
from ultralytics import YOLO

# 加载模型配置文件
model = YOLO("path/to/model.yaml")

# 加载数据集配置文件
model.train(data="path/to/data.yaml", cfg="path/to/train.yaml")

```

