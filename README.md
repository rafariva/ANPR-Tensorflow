# ANPR-TensorFlow

Using neural networks to build an automatic number plate recognition system. See [mattherwearl's blog post](http://matthewearl.github.io/2016/05/06/cnn-anpr/) for an explanation.

**NOTE:  This is an experimental project and is incomplete in a number of ways.** *This project is for be test it in Windows 10 64bits, and the code has been modify to generate licence plate patterns from **Ecuador**.*

## Dependencies:

- [Python v3.6.+ (64bits)](https://www.python.org/downloads/)
- NumPy v1.14.+
- Pillow v5.+
- OpenCV v3.14.+ (for cv2)
- MatPlotLib v2.1.+
- [TensorFlow v1.+](https://www.tensorflow.org/install/install_windows)

## Installations

Note: For install libraries use CMD terminal.

1. Download Python 3.6.+ (last version **of 64bits**), and install it. [Guide Video](https://www.youtube.com/watch?v=gSjL3K8C8Ao)
2. Installing numpy library (if not included)
```
py -m pip install numpy
```
3. Installing OpenCV library
```
py -m pip install opencv-python
```
4. Installing Pillow library
```
py -m pip install Pillow
```
5. Installing MatPlotLib
```
py -m pip install matplotlib
```
6. Installing TensorFlow (CPU or GPU) library
```
#*CPU version*
py -m pip install --upgrade tensorflow
```
or 
```
#*GPU version*
py -m pip install --upgrade tensorflow-gpu
```
For GPU Nvidia, must install [CUDA v9.0](https://developer.nvidia.com/cuda-90-download-archive?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exelocal) and [cuDNN v9.0](https://developer.nvidia.com/compute/machine-learning/cudnn/secure/v7.0.5/prod/9.0_20171129/cudnn-9.0-windows10-x64-v7) (for cuDNN follow [this steps](http://docs.nvidia.com/deeplearning/sdk/cudnn-install/index.html#install-windows))



## Project

Create a folder name `anpr` and copy the following py files and folders:
- `bgs\` (backgrounds images)
- `fonts\` (ttf file)
- `test\` (generated licence plate, _empty_)
- `common.py` (Common variables)
- `model.py` (py dependencie)
- `gen.py` (For generate test set images)
- `train.py` (For train the model with generate images)
- `detect.py` (For test result)


## Using Networks

Usage is as follows:

1. (optional but recommended) `./extractbgs.py SUN397.tar.gz`: Extract ~3GB of background images from the [SUN database](http://groups.csail.mit.edu/vision/SUN/) into `bgs/` (`bgs/` must be empty). The tar file (36GB) can be [downloaded here](http://vision.princeton.edu/projects/2010/SUN/SUN397.tar.gz). This step may take a while as it will extract 108,634 images.

2. `./gen.py`: Locate variable `generate_amount ` and set the number you want (default 100), it will safe the test set images in `test/` (`test/`must be empty). This step requires a `.ttf` files to be in the `fonts/` directory.

3. `./train.py`: Train the model. A **GPU** is recommended for this step. It will take around 100,000 batches to converge. When you're satisfied that the network has learned enough press Ctrl+C once and the process will create a `weights.npz` file and write the weights.

4. `./detect.py in.png CPUweights.npz out.png`: Detect number plates in an image and give and output image. if get a tensorflow gpu error, you should uninstall it `py -m pip unistall tensorflow-gpu`


Reproduce: [mattherwearl's deep-anpr](https://github.com/matthewearl/deep-anpr)
