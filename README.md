# ROBUSfT_fullCPU

ROBUSFT is a ready-to-use C++ library for monocular real-time 3D shape tracking of isometrically deforming objects. 
ROBUSFT forms a template from a deforming object and uses that to infer the deformation of the object in an input image (or a series of input images in a video). Each frame is processed independently. This makes ROBUSfT wide-baseline and resistant against losing the object in the video.  
This library is a full CPU version of the original [ROBUSfT](https://github.com/mrshetab/ROBUSfT) which is a CPU-GPU library. The original ROBUSfT is capable of tracking deformable objects up to 30fps while this speed is up to 20fps for this full CPU version.

## Dependencies

ROBUSfT_fullCPU depends on:

OpenCV

Eigen3

If you have a suitable cuda-adapted hardware and wish to increase the tracking speed, we recommend the CPU-GPU [ROBUSfT](https://github.com/mrshetab/ROBUSfT).

## Build

In order to build the library you can run the following commands:

```cmake
mkdir build && cd build
cmake ..
make
make install
```

## Usage

Two examples of the usage of this library are presented in the Folder "examples". 

* `Example1_RegularTemplate.cpp` this code shows how to set up a template with rectangular shape and regular mesh.

* `Example2_RegularTemplate.cpp` this code shows how to set up a template with nonrectangular shape and irregular mesh.

After building the files, the examples can run by executing the following the commands.

```cmake
# for the example with regular template
cd build/examples
./Example1_RegularTemplate

# for the example with irregular template
cd build/examples
./Example2_IrregularTemplate
```

The texture-maps for both examples can be found in the folder `Texturemaps`. 
Regarding the template with regular mesh, a Spiderman poster is selected as the texturemap. In the code, the number of mesh points in X and Y directions are chosen as 6 and 10, respectively. Foretheremore, the actual width of the object in X direction is set as 0.192m which is the width of the poster when is printed on an A4 paper.

As for the template with a nonrectangular shape and an irregular mesh, a shoe sole is chosen. Generally in these cases with an object with nonrectangular texturemaps, the texturemap of the object should be placed in the center of a totally white image as it is done for the shoe sole. The member function build_template will detach the textured region and generate a triangular mesh inside of that. Inside the code, the number of nodes on the boundary and inside of the texturemap will be chosen by the user. Foretheremore, the actual width of the object in X direction is set as 0.30m which is the length of the shoe sole in X direction.

The 3D coordinates of the object mesh in the camera coordinates frame are stored in the member variable `Shape_3d` as a 3xN vector where N denotes the number of mesh points. The projection of this 3D coordinates on the image is stored in the member variable `Shape_2d` as a 2xN vector. Both vectors can be printed using the function `show_array_2D()`. 

In order to switch the report (will be printed in terminal) and the plots on or off, the global boolean variable `ROBUSfT_report` and `ROBUSfT_plot` can be set. 


