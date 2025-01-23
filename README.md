This work is built on the repository https://github.com/Chan-Sun/IFSDD. Thanks for making it open source!

Check source code in the folder `defect`

## Installation

See [installation.md](packages/installation.md)

## Demo

### Videos
<video width="320" height="240" autoplay loop>
  <source src="assets/zoom_out_test.avi" type="video/avi">
  Your browser does not support the video tag.
</video>
<video width="320" height="240" autoplay loop>
  <source src="assets/scratches_detection.avi" type="video/avi">
  Your browser does not support the video tag.
</video>

### Images
![Image 1](assets/augmentation examples/brightness.png)
![Image 2](assets/augmentation examples/contrast.png)
![Image 3](assets/augmentation examples/fog.png)
![Image 4](assets/augmentation examples/rotation.png)
![Image 5](assets/augmentation examples/motion_blur.png)
![Image 6](assets/augmentation examples/zoom_blur.png)


## Training
Incremental learning consists of two stages:

![Image 1](assets/scheme1.jpg)

During inference different environmental conditions are applied.
![Image 2](assets/scheme2.jpg)

