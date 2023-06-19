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

For the data preparation for traditional NeRF dataset, please see [PointNeRF](https://github.com/Xharlie/pointnerf). We also show a pipeline to create your own dataset using [BlenderNeRF](https://github.com/maximeraafat/BlenderNeRF). This pipeline is only applicable to `nerf_synthetic` data, please put the dataset in the `./data_src/nerf/nerf_synthetic` folder. 

* Install [Blender](https://www.blender.org/download/) and [BlenderNeRF](https://github.com/maximeraafat/BlenderNeRF) add-on.

* Download our [Blender template](https://drive.google.com/file/d/1-k3-4-fvnN4Ct_t81ffOQ6Hs4TEf4_uQ/view?usp=sharing).

  ![template](./assets/template-1687211856773-9.png)

* Open the template, import the target object and rescale it such that the object is within the `BlenderNeRF Sphere`

  ![rescale](./assets/rescale-1687211852351-7.png)

* Press `space` to check the camera poses and scale are correct. You can set background to be transparent in `Film` option of `Render Properties` tag.

  ![check](./assets/check.gif)

* There are two options to generate dataset

  * Random camera pose around the sphere: Select `Camera on Sphere COS` option in `BlenderNeRF add-on`, chose `BlenderNeRF Camera`, run `PLAY COS`.

  * Continuous camera pose rotate w.r.t z-axis: Select `Subset of Frames SOF` option in `BlenderNeRF add-on`, chose `Test Camera`, run `PLAY SOF`.

* Decompress the zip file, open the `json` files, remove all suffix `.png`. And duplicate the `train` folder as `eval` folder and `test` folder, create corresponding `json` files (`transforms_eval.json`,  `transforms_test.json`)

* Create corresponding scripts (e.g. `dragon_cuda.sh` ), note that you only need to change the `name`, `scan` options first in the bash file.  

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
