This work is built on the repository https://github.com/Chan-Sun/IFSDD. Thanks for making it open source!

This repository contains the code for the Master's Thesis [**Visual Anomaly Detection in Industrial Environments Using Quadcopter's On-Board RGB Camera**](assets/VISUAL-ANOMALY-DETECTION.pdf)




Check source code in the folder `defect`



## Demo
<img src="assets/zoom_out_test.gif" width="60%" height="60%">
<img src="assets/scratches_detection.gif" width="60%" height="60%">

## Inference on inspection conditions
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
<img src="assets/scheme1.jpg" style="width: 60%; margin: auto; display: block;">

During inference different environmental conditions are applied.
<!-- <br> -->
<img src="assets/scheme2.jpg" style="width: 60%; margin: auto; display: block;">


## GUI for image augmentation
This GUI is designed to test the robustness of any model for different conditions applied on the input images. It visualizes the augmented images, and updates the configuration of the pipeline of test data, and generate a bash file containig the test commands to run testing on multiple configurations consequently. The default augmentations are: `none`, `gaussian_noise`, `shot_noise`, `impulse_noise`, `motion_blur`, `zoom_blur`, `snow`, `fog`, `brightness`, `contrast`, `elastic_transform`, `pixelate`, `jpeg_compression`, `speckle_noise`, `spatter`, `saturate`.
<br>
<br>
<img src="assets/GUI.png" style="width: 100%; margin: auto; display: block;">
