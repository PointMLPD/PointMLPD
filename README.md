# SCF-Net: Learning Spatial Contextual Features for Large-Scale Point Cloud Segmentation


![abstract](./img/abstract.png)

### (1) Setup

This code has been tested with Python 3.5, Tensorflow 1.11, CUDA 9.0 and cuDNN v7 on Ubuntu 16.04.

* Setup python environment
  ```
  conda create -n SCF-Net python=3.5
  source activate SCF-Net
  ```

* Clone the repository

* Install the requirements
  ```
  pip install -r requirements.txt
  sh compile_op.sh
  ```

* Download pertained models

  | Dataset                  |                                 Baidu Cloud           | 
  |--------------------------|-------------------------------------------------------|
  | S3DIS                    | https://pan.baidu.com/s/1QSdXmhuJYixxYFF70No4XQ: rw6m | 
  | Semantic3D               | https://pan.baidu.com/s/1rsbPDTUXH-4-XvDSb0K2-g: bzcz |

### (2) S3DIS

![S3DIS](./img/s3dis.png)

* Setup the dataset
  * Download the "Stanford3dDataset_v1.2_Aligned_Version.zip" at [S3DIS](https://docs.google.com/forms/d/e/1FAIpQLScDimvNMCGhy_rmBA2gHfDu3naktRm6A8BPwAWWDv-Uhm6Shw/viewform?c=0&w=1), and move the upcompressed folder to /data/S3DIS
  * Preparing the dataset
    ```
    python utils/s3dis_dp.py
    ```
* Training
  ```
  python s3dis_main.py --gpu 0 --mode train --test_area xxx
  ```
* Evaluation
  ```
  python s3dis_main.py --gpu 0 --mode test --test_area xxx --model_path='path_to_model'
  ```
* 6 fold cross validation
  ```
  a) train and predict
     sh s3dis_6fold.sh

  b) evaluate
     python s3dis_6fold_eval.py
  ```

### (3) Semantic3D

![Semantic3D](./img/semantic3d.png)

* Setup the dataset
  * Download the dataset
    ```
    sh utils/download_semantic3d.sh
    ```
  * Preparing the dataset
    ```
    python utils/semantic3d_dp.py
    ```
* Training
  ```
  python semantic3d_main.py --mode train --gpu 0
  ```
* Testing
  ```
  python semantic3d_main.py --mode test --gpu 0 --model_path='path_to_model'


### (5) Visualization

![S3DIS_VIS](./img/s3dis_vis.png)

![Semantic3D_VIS](./img/semantic3d_vis.png)

```

### Acknowledgment

Part of our code refers to the work [RandLA-Net](https://github.com/QingyongHu/RandLA-Net)

