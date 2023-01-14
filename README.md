# MindCon-10类常见美食图片分类

本赛题任务是对美食图片进行分类。数据来自真实的美食图片，包括包含中餐、西餐、甜点、粥类，每张图像中美食所占比例大于3/4，每张图片代表一类美食。

我们约定是个类别的名称用如下数字代替：

冰激凌:0  鸡蛋布丁:1  烤冷面:2  芒果班戟:3  三明治:4  松鼠鱼:5  甜甜圈:6  土豆泥:7  小米粥:8  玉米饼:9

本项目采用 resnet101 模型进行图片分类.



## 数据集

数据集下载：https://xihe.mindspore.cn/datasets/drizzlezyk/mindcon_food_classification

数据集下载后按以下文件目录放置：

```
└─dataset
   ├─images  # 解压后的训练数据集, 文件夹改名为images
      └─0  # 将美食类别名称改为对应的标签
      └─1
      └─...
   └─test
      └─images  # 解压后的测试数据集，文件夹改名为images
```



## 环境要求

- 硬件（Ascend910）
- 框架（MindSpore1.8.1）



## 脚本说明

```
├── mindcon_food
  ├── README.md                           // mindcon_food相关说明
  ├── dataset                             // 数据集
      ├── images						  // 训练数据集
      ├── test                            // 测试数据集
  ├── src
      ├── data                            // 数据集配置
          ├──augment                      // 数据增强
          ├──data_utils                   // modelarts运行时数据集复制函数文件
          ┕──food_image_dataset.py        // 数据集处理
      ├── args.py                         // 配置文件
      ├── callback.py                     // 自定义回调函数
      ├── utils.py                         
  ├── log                                 // 训练日志
  ├── resnet101_ckpt                      // 模型保存文件夹
  ├── result                              // 推理结果
  ├── train.py                            // 训练文件
  ├── inference.py                        // 推理文件
```



## 训练和推理

- 训练（可更改 `src/args.py` 文件自定义训练参数）

```shell
python train.py
```

- 推理

```shell
python inference.py
```

推理结果保存在 `result/resnet101_sorted_result.txt`

