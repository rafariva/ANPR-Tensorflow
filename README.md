# ANPR-Tensorflow

Using neural networks to build an automatic number plate recognition system. See [mattherwearl's blog post](http://matthewearl.github.io/2016/05/06/cnn-anpr/) for an explanation.

**NOTE:  This is an experimental project and is incomplete in a number of ways.** *This project is for be test it in Windows 10, the specific version Dependecies, and the code has been modify to generate licence plate patterns from **Ecuador**.*

## Dependencies:

- [Python 3.6.2 (64bits)](https://www.python.org/downloads/release/python-362/)
- Numpy
- OpenCV(cv2)
- [TensorFlow](https://www.tensorflow.org/install/install_windows)

## Installations

Note: For install libraries use CMD

1. Download Python 3.6.+ (last version **of 64bits**), and install it. [Guide Video](https://www.youtube.com/watch?v=gSjL3K8C8Ao)
2. Installing numpy library
```
py -m pip install numpy
```
3. Installing Opencv libraries
```
py -m pip install opencv-python
```
4. Installing TensorFlow library
```
py -m pip install --upgrade tensorflow
```

## Project

Create a folder name *ANPR* and copy de followin py files:
- common.py (Common variables)
- model.py (py dependencie)
- gen.py (For generate test set images)
- train.py (For train the model with generate images)
- detect.py (For test result)


## Using Networks

Usage is as follows:

1. (optional but recommended) ./extractbgs.py SUN397.tar.gz: Extract ~3GB of background images from the SUN database into bgs/. (bgs/ must not already exist.) The tar file (36GB) can be downloaded here. This step may take a while as it will extract 108,634 images.

2. ./gen.py 1000: Generate 1000 test set images in test/. (test/ must not already exist.) This step requires UKNumberPlate.ttf to be in the fonts/ directory, which can be downloaded here.

3. ./train.py: Train the model. A GPU is recommended for this step. It will take around 100,000 batches to converge. When you're satisfied that the network has learned enough press Ctrl+C and the process will write the weights to weights.npz and return.

4. ./detect.py in.jpg weights.npz out.jpg: Detect number plates in an image.


Reproduce: [mattherwearl's deep-anpr](https://github.com/matthewearl/deep-anpr)
