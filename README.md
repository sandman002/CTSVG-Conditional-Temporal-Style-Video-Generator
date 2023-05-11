# MyVideoGeneration [WIP]
Conditional video generation with style

## Changing emotion mid sequence

![alt text](./anim/emotion_chain.gif)

## Gan inversion of motion styles

![alt text](./anim/fake_projected.gif)

## Requirements
- Ubuntu 20.04.3 LTS (GNU/Linux 5.4.0-91-generic x86_64)
- CUDA Version: 11.5
- Python>=3.8

## Environment Setup

```
conda create -n CTSVG python=3.8
conda activate CTSVG

pip install torch==1.7.1+cu110 torchvision==0.8.2+cu110 torchaudio===0.7.2 -f https://download.pytorch.org/whl/torch_stable.html
pip install opencv-python tqdm pandas scipy scikit-learn
```

## Dataset

### Structure
Following is the directory structure for MEAD dataset.
```
MEAD
|-- M003_front
    |-- angry
        |-- level_1
            |-- 001
                |-- frame0000.jpg
                |-- frame0001.jpg
                |-- ...
            |-- 002
            |-- 003
            |-- ...
        |-- level_2
        |-- level_3
    |-- contempt
        |-- level_1
        |-- level_2
        |-- level_3
    |-- disgusted
    |-- fear
    |-- happy
    |-- neutral
    |-- sad
    |-- surprised
|-- M007_front
|-- W019_front
|-- ...
```
Following is the directory structure for UTD-MHAD dataset.
```
UTD-MHAD
|-- train
    |-- a1
        |-- a1_s2_t1_color
            |-- frame0000.jpg
            |-- frame0001.jpg
            |-- ...
        |-- a1_s2_t2_color
            |-- frame0000.jpg
            |-- frame0001.jpg
            |-- ...
        |-- ...
    |-- a2
    |-- ...
    |-- a27
|-- val
    |-- a1_s1_t1_color
        |-- frame0000.jpg
        |-- frame0001.jpg
        |-- ...
    |-- a1_s1_t2_color
    |-- ...
```
Following is the directory structure for RAVDESS dataset.
```
RAVDESS
|-- Actor_01
    |-- 02-01-01-01-01-01-01
        |-- frame0000.jpg
        |-- frame0001.jpg
        |-- ...
    |-- 02-01-01-01-01-02-01
    |-- 02-01-07-01-02-01-01
    |-- ...
|-- Actor_02
|-- Actor_03
|-- Actor_04
|-- ...     
```

### Dataset download
- MEAD (coming soon)
- RAVDESS (coming soon)
- UTD-MHAD (coming soon)

## Training
```
python train.py --chkpath ./checkpoint_path --samplepath ./sample_path --size 128 --num_person 30 --num_classes 8 --batch 16
```
Resume training
```
python train.py --ckpt ./checkpoint_path/XXXX.pt --chkpath ./checkpoint_path --samplepath ./sample_path --size 128 --num_person 30 --num_classes 8 --batch 16
```
## Generate (Inference)
```
python generate.py --ckpt ./checkpoint_path/XXXX.pt --savepath ./save_path --size 128 --num_person 30 --num_classes 8 
```
## GAN-Inversion
```
python project.py --ckpt ./checkpoint_path/XXXX.pt --savepath ./save_path --size 128 --num_person 30 --num_classes 8 
```
