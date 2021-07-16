# Overview
This repository contains our team([randomTeamName](https://www.aicrowd.com/challenges/global-wheat-challenge-2021/teams/randomTeamName))'s first place solution of the [Global Wheat Challenge 2021](https://www.aicrowd.com/challenges/global-wheat-challenge-2021). <!-- comprised of [ksnxr](https://www.aicrowd.com/participants/ksnxr) and [czz1997](https://www.aicrowd.com/participants/czz1997). -->

# Get Started
Please first make sure you have `Python 3.7.10` installed to reproduce our result, since this is the Python version on Google Colab Pro where we run most of our experiments. If you want to experiment on your own, please refer to [this](https://github.com/ultralytics/yolov5#quick-start-examples) for Python version requirement.

1. clone this repo and our customized YOLOv5 repo.
    ```
    $ git clone https://github.com/ksnxr/GWC_solution.git
    $ cd GWC_solution && git clone https://github.com/ksnxr/GWC_YOLOv5.git
    ```
2. install required dependencies.
    * We require specific version of the following packages to reproduce our result:

        * PyTorch: 1.9.0+cu102
        * TorchVision: 0.10.0+cu102
        * numpy: 1.19.5
        * scipy: 1.4.1
    
        You can install these packages by:
        ```
        $ cd GWC_solution && pip install requirements.txt
        ```
    * If you are using Google Colab, most of the other dependencies should be in place, except PyYAML and ensemble_boxes. You can install them by:
        ```
        !pip uninstall -y PyYAML
        !pip install PyYAML==5.3.1
        !pip install ensemble_boxes
        ```
    * Otherwise, please run the following command to install all the required dependencies:
        ```
        $ cd GWC_solution/GWC_YOLOv5 && pip install requirements.txt
        ```

# Steps To Reproduce

## Train From Start
<!--0. Download this repo and run `git clone https://github.com/ksnxr/GWC_YOLOv5.git` to clone the customized YOLOv5.-->
1. Use [KFold.ipynb](KFold.ipynb) to generate 4-folds train and validation indexes.
2. Use [basis-0.ipynb](basis/basis-0.ipynb), [basis-1.ipynb](basis/basis-1.ipynb), [basis-2.ipynb](basis/basis-2.ipynb) and [basis-3.ipynb](basis/basis-3.ipynb) to train on the four folds.
3. Use [pseudo-original-0.ipynb](pseudo/pseudo-original-0.ipynb), [pseudo-original-1.ipynb](pseudo/pseudo-original-1.ipynb), [pseudo-original-2.ipynb](pseudo/pseudo-original-2.ipynb), [pseudo-original-3.ipynb](pseudo/pseudo-original-3.ipynb) and [pseudo-master-3.ipynb](pseudo/pseudo-master-3.ipynb) to train 5 pseudo models.
4. Use [get-labels.ipynb](get-labels.ipynb) to ensemble the 5 weights obtained in step 3 and generate labels for subsequent training.
5. Use [pseudo-master-final.ipynb](pseudo-master-final.ipynb) to train the final model.

The final single model yields [**0.700**](https://www.aicrowd.com/challenges/global-wheat-challenge-2021/submissions/149238) on the final private leaderboard.

## Use Our Trained Model
If you find it time-consuming to train models, we also provide our trained models so that you can simply run the inference code. You can access our trained models from here(We will upload them soon).

# Experiment On Your Own
If you would like to do some experiments on our solution, we also provide our general training and inference notebooks. 

<!--
# Environment
A huge amount of the computation was powered by Google Colab Pro.

We ran our code under the following environment:

* Python: 3.7.10
* PyTorch: 1.9.0+cu102
* TorchVision: 0.10.0+cu102
* numpy: 1.19.5
* scipy: 1.4.1
-->

# Acknowledgement

We would like to thank those who inspired us with open source solutions, including: 

* [Ultralytics](https://github.com/ultralytics) for their [YOLOv5 repository](https://github.com/ultralytics/yolov5)
* [ZFTurbo](https://github.com/zfturbo) for his [weighted boxes fusion repository](https://github.com/ZFTurbo/Weighted-Boxes-Fusion)
* [nvnn](https://www.kaggle.com/nvnnghia) for his [pseudo labeling notebook](https://www.kaggle.com/nvnnghia/yolov5-pseudo-labeling)