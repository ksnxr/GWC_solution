# Overview
This repository contains the first place solution of the [Global Wheat Challenge 2021](https://www.aicrowd.com/challenges/global-wheat-challenge-2021) competition, from the team [randomTeamName](https://www.aicrowd.com/challenges/global-wheat-challenge-2021/teams/randomTeamName), comprised of [ksnxr](https://www.aicrowd.com/participants/ksnxr) and [czz1997](https://www.aicrowd.com/participants/czz1997).

# Acknowledgement

We would like to thank those who inspired us with open source solutions, including: 

* [Ultralytics](https://github.com/ultralytics) for their [YOLOv5 repository](https://github.com/ultralytics/yolov5)
* [ZFTurbo](https://github.com/zfturbo) for his repository on [weighted boxes fusion](https://github.com/ZFTurbo/Weighted-Boxes-Fusion)
* [nvnn](https://www.kaggle.com/nvnnghia) for his [notebook on pseudo labeling](https://www.kaggle.com/nvnnghia/yolov5-pseudo-labeling).


# Steps to reproduce
1. Use [KFold.ipynb](KFold.ipynb) to generate 4-folds train and validation indexes.
2. Use [basis-0.ipynb](basis/basis-0.ipynb), [basis-1.ipynb](basis/basis-1.ipynb), [basis-2.ipynb](basis/basis-2.ipynb) and [basis-3.ipynb](basis/basis-3.ipynb) to train on the four folds.
3. Use [pseudo-original-0.ipynb](pseudo/pseudo-original-0.ipynb), [pseudo-original-1.ipynb](pseudo/pseudo-original-1.ipynb), [pseudo-original-2.ipynb](pseudo/pseudo-original-2.ipynb), [pseudo-original-3.ipynb](pseudo/pseudo-original-3.ipynb) and [pseudo-master-3.ipynb](pseudo/pseudo-master-3.ipynb) to train 5 pseudo models.
4. Use [get-labels.ipynb](get-labels.ipynb) to ensemble the 5 weights obtained in step 3 and generate labels for subsequent training.
5. Use [pseudo-master-final.ipynb](pseudo-master-final.ipynb) to train the final model.

The final single model yields [**0.700**](https://www.aicrowd.com/challenges/global-wheat-challenge-2021/submissions/149238) on the final private leaderboard.
# Environment
A huge amount of the computation was powered by Google Colab Pro.

We ran our code under the following environment:

* Python: 3.7.10
* PyTorch: 1.9.0+cu102
* TorchVision: 0.10.0+cu102
* numpy: 1.19.5
* scipy: 1.4.1