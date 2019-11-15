# Manual installation to use Kinect V2 with SimpleOpenni

> If you are using Kinect V1 avoid this steps and just download and paste the library in the the Processing folder

<img src="Assets/threshold.gif" width="900">

<img src="Assets/Kinect_V2_Tracking.gif" width="900">

   > Example of skeleton tracking using KinectV2

### Mac OS

* Install [Homebrew](https://brew.sh/index_es) opening a terminal and pasting the next code

``` terminal
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
> The site that is provided in the link is in Spanish

- Make sure these build tools are available:
  - wget
  - git
  - cmake
  - pkg-config

> If you don't have the tools use Homebrew to install them

- Open a terminal and download libfreenect2 source
  ```
  git clone https://github.com/OpenKinect/libfreenect2.git
  cd libfreenect2
  ```

- Open an other terminal and install dependencies:
  ```
  brew update
  brew install libusb
  brew tap homebrew/versions
  brew install glfw3
  ```

- Install TurboJPEG (optional)
  ```
  brew install jpeg-turbo
  ```

- Install CUDA (optional): TODO

- Return to the first terminal, or in the libfreenect2 folder, and build:
  ```
  mkdir build && cd build
  cmake ..
  make
  make install
  ```

- Install OpenNI2 (optional)
  ```
  brew tap brewsci/science
  brew install openni2
  export OPENNI2_REDIST=/usr/local/lib/ni2
  export OPENNI2_INCLUDE=/usr/local/include/ni2
  ```

### Common errors

   If you got this error after run the skeleton example:

   ```
   SimpleOpenNI Version 1.96
   After initialization:

   SimpleOpenNI Error: Can't open device:		DeviceOpen using default: no devices found


   SimpleOpenNI not initialised
   ```
   
   Copy manually the file `libfreenect2/build/lib/libfreenect2-openni2.0.dylib` into the Processing SimpleOpenNI library folder.

### Linux (Kinect v1, models 1414, 1473)

This version work with the following Ubuntu Linux distributions: 18.04. 19.04 and 19.10
This pluging works with this file version: libboost_system.so.1.54.0
The steps are the following:

    1- Install libfreenect
    2- locate libboost_system.so 1.5* to get the path of ibboost_system and to find the version installed of it.
    3 Create a soft link as libboost_system.so.1.54.0.
    4- Assuming the path could be usr/lib/x86_64-linux-gnu/, the command to create the soft link will be
    sudo ln -s /usr/lib/x86_64-linux-gnu/libboost_system.so.1.67.0 /usr/lib/x86_64-linux-gnu/libboost_system.so.1.54.0
    5- Install the library in the sketchbook folder as usual

Source: https://github.com/totovr/SimpleOpenNI/issues/24 

Thanks to https://github.com/pointcloudAI for the clue
