# docker_ubuntu1804_gpu_ros_melodic
Dockerfile to build docker image of Ubuntu 18.04 which recognizes GPU and ROS Melodic is installed.

## What is this?
You can build and run a docker image/container of Ubuntu 18.04 which has ROS Melodic. In the container, GPU can be used and GUI applications like rviz can be displayed. I hope this repository will make your ROS environment setting up more efficient.  

## Supported platforms
Currently, only WSL2 on Windows11 is supported.  

## Requirements
## OS
To install Docker Engine, you need the 64-bit version of Ubuntu as follow.  

* Ubuntu Lunar 23.04
* Ubuntu Kinetic 22.10
* Ubuntu Jammy 22.04 (LTS)
* Ubuntu Focal 20.04 (LTS)

## Applications
The following applications need to be installed in advance.  

* [Visual Studio Code](https://code.visualstudio.com/)
* [Docker](https://docs.docker.com/engine/install/ubuntu/)
* [NVIDIA Driver](https://www.nvidia.co.jp/Download/index.aspx?lang=jp)
* [nvidia-container-runtime](https://github.com/NVIDIA/nvidia-container-runtime)

