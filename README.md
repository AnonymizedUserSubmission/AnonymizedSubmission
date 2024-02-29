## Table of Contents
- [Introduction](#Introduction)
- [Requirements](#Requirements)
- [Installation](#Installation)
- [Pretrained Models](#Pretrained-Models)
- [Data Preparation](#Data-Preparation)
- [Demo](#Demo)
- [Training](#Training)
- [Evaluation](#Evaluation)
- [References](#References)


## Introduction
This repository provides the code for the anonymized submission "FakeMix Augmentation Improves Transparent Object Detection".

## Requirements
- python3
- PyTorch=1.1.0
- torchvision
- Pillow
- numpy
- pyyaml

## Installation

Please make sure that there is at least one gpu when compiling. Then run:

- `python3 setup.py develop`

## Pretrained Models
All the pretrained models can be fould here:
[PretrainModels](https://github.com/AnonymizedUserSubmission/AnonymizedSubmissionForFANet/tree/main/workdirs).


## Data Preparation
1. create dirs './datasets/Trans10K'
2. download the data from [Trans10K](https://xieenze.github.io/projects/TransLAB/TransLAB.html) [1].
3. put the train/validation/test data under './datasets/Trans10K'.
The data Structure is shown below:

```
Trans10K/
├── test
│   ├── easy
│   └── hard
├── train
│   ├── images
│   └── masks
└── validation
    ├── easy
    └── hard
```

## Demo
```
CUDA_VISIBLE_DEVICES=0 python3 -u ./tools/test_demo.py --config-file configs/trans10K/trans10K.yaml DEMO_DIR ./demo/imgs
```

## Training
```
bash tools/dist_train.sh configs/trans10K/trans10K.yaml 8
```

## Evaluation
```
CUDA_VISIBLE_DEVICES=0 python3 -u ./tools/test_translab.py --config-file configs/trans10K/trans10K.yaml 
```

## References
1. Xie, E., Wang, W., Wang, W., Ding, M., Shen, C., Luo, P.: Segmenting transparent objects in the wild. In ECCV, 2020.
