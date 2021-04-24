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

- First, please download the [ImageNet100](baidunetdisk) and [Cifar100](baidunetdisk).
Please put the downloaded files into the `data` directory like this:
```
data
  |--ImageNet100
    |--ImageNet100-IF1
    |--ImageNet100-IF10
    |--ImageNet100-IF20
    |--ImageNet100-IF50
    |--ImageNet100-IF100
  |--Cifar100
    |--Cifar100-IF1
    |--Cifar100-IF10
    |--Cifar100-IF20
    |--Cifar100-IF50
    |--Cifar100-IF100
```
Please also change the `data_root` in `main.py` accordingly.


## Training & Testing

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
