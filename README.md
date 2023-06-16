# PointNeRF-Assistant
## Overview

This is a repository is an assistant to set up PointNeRF. We set up a stable environment for point-nerf for ubuntu 20.04, and modified point-nerf code to fix some bug during running. We also share a pipeline to generate your own dataset using [BlenderNeRF](https://github.com/maximeraafat/BlenderNeRF). We extends from the original repository of [PointNeRF](https://github.com/Xharlie/pointnerf).

## Installation

### Requirements

All the codes are tested in the following environment: Python 3.8; Ubuntu 20.04; CUDA > 11.7.

### Install

* Install the environment from `yml`:

  ```bash
  conda env create -f environment.yml
  ```

* In mainland China:

  ```
  conda env create -f environment_autodl.yml
  ```
  
* Install `pytorch3d`

  ```bash
  conda activate point-nerf
  pip install fvcore iopath
  pip install --no-index --no-cache-dir pytorch3d -f https://dl.fbaipublicfiles.com/pytorch3d/packaging/wheels/py39_cu117_pyt1131/download.html
  ```

## Data Preparation

For the data preparation for traditional NeRF dataset, please see [PointNeRF](https://github.com/Xharlie/pointnerf). We also show a pipeline to create your own dataset using [BlenderNeRF](https://github.com/maximeraafat/BlenderNeRF). 

## Initialization and Optimization

### Download pre-trained MVSNet checkpoints:

You can Download ''MVSNet'' directory from [google drive](https://drive.google.com/drive/folders/1xk1GhDhgPk1MrlX8ncfBz5hNMvSa9vS6?usp=sharing) and place them under `checkpoints/`. Please check [PointNeRF](https://github.com/Xharlie/pointnerf) for more details. 

### Per-scene optimize from scatch

This environment only supports `pytorch3d` implementations:

<details>
  <summary>train scripts</summary>

```
    bash dev_scripts/w_n360/chair_cuda.sh
    bash dev_scripts/w_n360/drums_cuda.sh
    bash dev_scripts/w_n360/ficus_cuda.sh
    bash dev_scripts/w_n360/hotdog_cuda.sh
    bash dev_scripts/w_n360/lego_cuda.sh
    bash dev_scripts/w_n360/materials_cuda.sh
    bash dev_scripts/w_n360/mic_cuda.sh
    bash dev_scripts/w_n360/ship_cuda.sh
```
</details>

## Acknowledgement

This repo is developed based on [PointNeRF](https://github.com/Xharlie/pointnerf). Please cite the corresponding papers. 

```
@inproceedings{xu2022point,
  title={Point-nerf: Point-based neural radiance fields},
  author={Xu, Qiangeng and Xu, Zexiang and Philip, Julien and Bi, Sai and Shu, Zhixin and Sunkavalli, Kalyan and Neumann, Ulrich},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  pages={5438--5448},
  year={2022}
}
```

## LICENSE

The code is released under the GPL-3.0 license.
