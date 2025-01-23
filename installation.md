
## installation

1. Create conda environment

```shell
conda create --name defect python=3.8 -y
conda activate defect
```

2. Install `Pytorch` with cuda

```shell
pip install torch==1.9.0+cu111 torchvision==0.10.0+cu111 torchaudio==0.9.0 -f https://download.pytorch.org/whl/torch_stable.html
```

3. Install `MMCV` and `MMCLS`

```shell
pip install -U openmim
mim install mmcv-full==1.4.6
pip install mmcls==0.16
pip install mmdet
```


In case weights of ResNet are not found, download resnet101 weights from openmmlab model zoo and put it to the hidden directory ```~/.torch/models```

