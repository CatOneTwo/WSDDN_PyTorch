# WSDDN PyTorch
This repository contains the PyTorch implementation of paper [`Weakly Supervised Deep Detection Networks`](https://arxiv.org/abs/1511.02853) (CVPR 2016)

Implementation differences: Spatial regulariser isn't added

## Architecture
![WSSSN](https://raw.githubusercontent.com/CatOneTwo/Picbed_PicGo/master/img/WSDDN.png)

## Contents
1. [Requirements: software](#requirements-software)
2. [Requirements: hardware](#requirements-hardware)
3. [Basic installation](#basic-installation)
4. [Installation for training and testing](#installation-for-training-and-testing)
5. [Extra Downloads (selective search)](#extra-downloads-selective-search)
6. [Extra Downloads (ImageNet models)](dxtra-downloads-imageNet-models)
7. [Usage](#usage)


## Requirements: software
Python3 packages and versions used (listed using freeze frin pip) are in requirements.txt.

You can create a new virtual environment and then install thses packages from requirements.txt.
```shell
conda create -n env_name python=3.6
pip install -r $WSDDN_ROOT/requirements.txt
```
You can also install these packages by yourself.
## Requirements: hardware
- We used cuda 9.0 and cudnn 7.0
    - We used an Nvidia GeForce GTX with 10.9G of memory. But it shold be ok to train if you have a GPU with at least 8Gb.
    - **NOTICE**: different versions of Pytorch have different memory usages.

## Basic installation
Clone this repository
```shell
git clone https://github.com/CatOneTwo/WSDDN-PyTorch && cd WSDDN
```
## Installation for training and testing
1. Create a "data" folder in  $WSDDN_ROOT and enter in this folder
    ```Shell
    cd $WSDDN_ROOT
    mkdir data
    cd data
    ```
2. Download the training, validation, test data, and VOCdevkit
    ```Shell
    wget https://pjreddie.com/media/files/VOCtrainval_06-Nov-2007.tar
    wget https://pjreddie.com/media/files/VOCtest_06-Nov-2007.tar
    ```
3. Extract all of these tars into one directory named `VOCdevkit`
    ```Shell
    tar xvf VOCtrainval_06-Nov-2007.tar
    tar xvf VOCtest_06-Nov-2007.tar
    ```
4. Download the VOCdevkit evaluation code adapted to octave
    ```Shell
    wget http://inf.ufrgs.br/~lfazeni/CVPR_deepvision2020/VOCeval_octave.tar
    ```
5. Extract VOCeval_octave
    ```Shell
    tar xvf VOCeval_octave.tar
    ```
6. Download pascal annotations in the COCO format
    ```Shell
    wget http://inf.ufrgs.br/~lfazeni/CVPR_deepvision2020/coco_annotations_VOC.tar
    ```
7. Extract the annotations
    ```Shell
    tar xvf coco_annotations_VOC.tar
    ```
8. It should have this basic structure
    ```Shell
    $VOC2007/                           
    $VOC2007/annotations
    $VOC2007/JPEGImages
    $VOC2007/VOCdevkit        
    # ... and several other directories ...
    ```
9. [Optional] download and extract PASCAL VOC 2012.
    ```Shell
    wget http://host.robots.ox.ac.uk/pascal/VOC/voc2012/VOCtrainval_11-May-2012.tar
    tar xvf VOCtrainval_11-May-2012.tar
    ```
    **Observation:** The  `2012 test set` is only available in the [PASCAL VOC Evaluation Server](http://host.robots.ox.ac.uk:8080/) to download. You must create a user and download it by yourself. After downloading, you can extract it in the data folder.
## Extra Downloads (selective search)
1. Download the proposals data generated by selective search to data folder
    ```Shell
    wget http://inf.ufrgs.br/~lfazeni/CVPR_deepvision2020/selective_search_data.tar
    ```
2. Extract the proposals
    ```Shell
    tar xvf selective_search_data.tar
    ```

## Extra Downloads (ImageNet models)
1. Download the pre-trained VGG16 model to data folder
    ```Shell
    wget http://inf.ufrgs.br/~lfazeni/CVPR_deepvision2020/pretrained_model.tar
    ```
2. Extract the pre-trained VGG16 model 
    ```Shell
    tar xvf pretrained_model.tar
    ```
## Usage

---

## Note
Below is the code structure

- code
    - datasets: VOC dataset file
    - layers: layer and loss files
    - models: WSDDN model based on layers
    - tasks: train, test and visualize files
    - utils: files used for other directories
- configs
    - baselines: config files for model and dataset
- data
    - pretrained_model: VGG16 model weights
    - selective_search_data: selective search for VOC data
    - VOCdevikit: VOC dataset

All code files are in `code` directory. If you want to design a model based on WSDDN, you can modify `layers` and `model`.
