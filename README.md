# Long-Tail Hashing

[[Paper]](https://) 

## Overview
`LTH Net` is the author's re-implementation of the long-tail hashing network described in:  
"[Long-Tail Hashing](https://arxiv.org/abs/****)"   
[Yong Chen](https://zero-lab-pku.github.io/personwise/chenyong/),&nbsp; [Yuqing Hou],&nbsp; [Shu Leng],&nbsp; [Qing Zhang],&nbsp; [Zhouchen Lin](https://zhouchenlin.github.io/),&nbsp; [Dell Zhang](https://www.dcs.bbk.ac.uk/~dell/)&nbsp; &nbsp; 
in ACM Special Interest Group on Information Retrieval (SIGIR) 2021, **Full Paper**

<img src='./LTHNet.png' width=800>

Further information please contact [Yong Chen](mailto:butterfly.chinese@pku.edu.cn).

## Update notifications
* __**/**/2021:__ We ***

## Requirements
* [PyTorch](https://pytorch.org/) (version >= ？)
* [scikit-learn](https://scikit-learn.org/stable/)

## Data Preparation

- First, please download the ImageNet100 and [Cifar100](https://www.cs.toronto.edu/~kriz/cifar.html).
Please also change the `data_root` in `main.py` accordingly.

- Next, please download ImageNet-LT and Places-LT from [here](https://drive.google.com/drive/u/1/folders/1j7Nkfe6ZhzKFXePHdsseeeGI877Xu1yf). Please put the downloaded files into the `data` directory like this:
```
data
  |--ImageNet_LT
    |--ImageNet_LT_open
    |--ImageNet_LT_train.txt
    |--ImageNet_LT_test.txt
    |--ImageNet_LT_val.txt
    |--ImageNet_LT_open.txt
  |--Places_LT
    |--Places_LT_open
    |--Places_LT_train.txt
    |--Places_LT_test.txt
    |--Places_LT_val.txt
    |--Places_LT_open.txt
```

## Download Caffe Pre-trained Models for Places_LT Stage_1 Training
* Caffe pretrained ResNet152 weights can be downloaded from [here](https://drive.google.com/uc?export=download&id=0B7fNdx_jAqhtckNGQ2FLd25fa3c), and save the file to `./logs/caffe_resnet152.pth`

## Getting Started (Training & Testing)

<img src='./assets/pipeline.png' width=800>

### ImageNet100
- Stage 1 training:
```
python main.py --config ./config/ImageNet_LT/stage_1.py
```
- Stage 2 training:
```
python main.py --config ./config/ImageNet_LT/stage_2_meta_embedding.py
```


### Cifar100
- Stage 1 training (At this stage, multi-GPU might be necessary since we are finetuning a ResNet-152.):
```
python main.py --config ./config/Places_LT/stage_1.py
```
- Stage 2 training (At this stage, only single-GPU is supported, please switch back to single-GPU training.):
```
python main.py --config ./config/Places_LT/stage_2_meta_embedding.py
```


## Reproduced Benchmarks and Model Zoo (Updated on 03/05/2020)

### ImageNet-LT Open-Set Setting

|   Backbone  |    Many-Shot   |  Medium-Shot  |   Few-Shot  |  F-Measure  |      Download      |
| :---------: | :------------: | :-----------: | :---------: | :---------: | :----------------: |
|  ResNet-10  |      44.2      |      35.2     |    17.5     |     44.6    |     [model](https://drive.google.com/open?id=1CKcZuTQJkRvA3pUK_AL_H2wsvt5gY5of)      |

### Places-LT Open-Set Setting

|   Backbone  |    Many-Shot   |  Medium-Shot  |   Few-Shot  |  F-Measure  |      Download      |
| :---------: | :------------: | :-----------: | :---------: | :---------: | :----------------: |
| ResNet-152  |      43.7      |      40.2     |    28.0     |     50.0    |     [model](https://drive.google.com/open?id=1ZkYzg74O8hKlsq8LcLlECsi2QVeG5mr0)      |

## CAUTION
The current code was prepared using single GPU. 

## License and Citation
The use of this software is released under [BSD-3](https://github.com/zhmiao/OpenLongTailRecognition-OLTR/blob/master/LICENSE).
```
TODO
BIB for the paper
```
