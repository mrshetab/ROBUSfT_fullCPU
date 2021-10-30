# ROBUSfT_fullCPU

ROBUSFT is a ready-to-use C++ library for monocular real-time 3D shape tracking of isometrically deforming objects. ROBUSFT forms a template from a deforming object and using that, it infers the deformation of the object in an input image (or a series of input images in a video). Each frame is processed indivisually. This makes ROBUSfT wide-baseline and resistant against losing the object in the video.
This library is a ful CPU version of the [ROBUSfT](asdf.com) library. The original ROBUSfT is capable of tracking deformable objects up to 30fps. This speed is 20fps for this full CPU version.

## Dependencies

ROBUSfT_fullCPU depends on:

OpenCV

Eigen3

If you have a suitable Cuda-adapted hardware and wish to increase the tracking speed, we recommend the CPU-GPU [ROBUSfT].

## Build

In order to build the library you can run the following commands:

```cmake
mkdir build && cd build
cmake ..
make
make install
```


## Usage



