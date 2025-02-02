This repository contains the code for the Master's Thesis [**Visual Anomaly Detection in Industrial Environments Using Quadcopter's On-Board RGB Camera**](assets/VISUAL-ANOMALY-DETECTION.pdf) [[PDF]](assets/VISUAL-ANOMALY-DETECTION.pdf)




Check out source code in the folder `defect`

## Demo

<div style="display: flex; flex-wrap: wrap; justify-content: center;">
  <img src="assets/zoom_out_test.gif" style="width: 100%; height: 100%;">
  <img src="assets/scratches_detection.gif" style="width: 100%; height: 100%;">
</div>
<br>

Inspection on a close surface:
<div align="center">
<img src="assets/inclusion.jpg" style="width: 50%; height: 50%;">
</div>
<br>

Inference on inspection conditions:
`brightness`, `contrast`, `fog`, `rotation`, `motion blur`, `zoom blur`
<br>
<br>
<div style="display: flex; flex-wrap: wrap;">
  <img src="assets/augmentation-examples/brightness.png" style="width: 30%;">
  <img src="assets/augmentation-examples/contrast.png" style="width: 30%;">
  <img src="assets/augmentation-examples/fog.png" style="width: 30%;">
  <img src="assets/augmentation-examples/rotation.png" style="width: 30%;">
  <img src="assets/augmentation-examples/motion_blur.png" style="width: 30%;">
  <img src="assets/augmentation-examples/zoom_blur.png" style="width: 30%;">
</div>

## Installation

See [installation.md](installation.md)

## Incremental Learning
The model is able to learn new defects incrementally. The training paradigm consists of two stages:
<!-- <br> -->
<div align="center">
<img src="assets/fine_tune_pipeline.jpg" style="width: 80%; margin: auto; display: block;">
</div>


## Fine-tuning
When training Faster RCNN then fine-tuning it directly, the `catastrophic forgetting` phenomenon was observed.
<br>
1. The model is trained on 3 categories of defects.
2. The model is fine-tuned on 3 additional categories of defects.
<br>
**Observation:** When the model learns new defects, it forgets the old ones.
<br>
We see the drop in accuracy from: 86%, 90%, 94% to 67%, 64%, 64%.
<div style="display: flex; flex-wrap: wrap; justify-content: center;">
  <img src="assets/Pretrained Faster RCNN.png" style="width: 40%;">
  <img src="assets/confusion_after_finetune.png" style="width: 40%;">
</div>

## Fine-tuning with knowledge distillation
To deal with catastrophic forgetting, the DKAN framework was used.
This framework is taken from https://github.com/Chan-Sun/IFSDD. Thank you for making the code available.
<br>
It creates two copies of the model, and uses the teacher-student paradigm based on knowledge distillation to remind the model of its previous knowledge.
<div align="center">
<img src="assets/fine_tuning_with_KD.png" style="width: 80%; margin: auto; display: block;">
</div>

## Stopping Catastrophic Forgetting
DKAN (Yellow) <br>
FSCE (light blue) <br>
Direct fine-tuning (dark blue)

<div align="center">
<img src="assets/fine_tune_comparison.png" style="width: 100%; margin: auto; display: block;">
</div>

DkAN could successfully maintain a constant performance (mAP) after fine-tuning.

## GUI for image augmentation
This GUI is designed to test the robustness of any model for different conditions applied on the input images. It visualizes the augmented images, and updates the configuration of the pipeline of test data, and generate a bash file containig the test commands to run testing on multiple configurations consequently. The default augmentations are: `none`, `gaussian_noise`, `shot_noise`, `impulse_noise`, `motion_blur`, `zoom_blur`, `snow`, `fog`, `brightness`, `contrast`, `rotation`, `elastic_transform`, `pixelate`, `jpeg_compression`, `speckle_noise`, `spatter`, `saturate`.
<br>
<br>
<img src="assets/GUI.png" style="width: 100%; margin: auto; display: block;">

## Additional experiment: Mixture-of-Experts
Mixture of experts was incorporated into the last two layers of the ROI head. The results were identical. Check out the code in the folder `moe`.
<div align="center">
<img src="assets/moe_head.jpg" style="width: 80%; margin: auto; display: block;">
</div>