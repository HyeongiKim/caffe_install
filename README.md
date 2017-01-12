#Caffe Installation for Ubuntu 16.04

###Before start

    sudo apt update
    sudo apt upgrade
    sudo apt install build-essential git cmake cmake-gui

###General dependencies

    sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler
    sudo apt-get install --no-install-recommends libboost-all-dev

###CUDA

- Check version

    nvcc --version

- If none, go to https://github.com/facebook/fbcunn/blob/master/INSTALL.md

####Install CUDA

    sudo apt-get install build-essential

Download installer for Ubuntu 16.04 x86

    https://developer.nvidia.com/cuda-downloads

Installation instructions

    sudo dpkg -i cuda-repo-ubuntu1604-8-0-local_8.0.44-1_amd64.deb
    sudo apt-get update
    sudo apt-get install cuda
    echo "export PATH=/usr/local/cuda/bin/:\$PATH; export LD_LIBRARY_PATH=/usr/local/cuda/lib64/:\$LD_LIBRARY_PATH; " >>~/.bashrc && source ~/.bashrc

Restart your computer

####Install CuDNN

Go to https://developer.nvidia.com/cuDNN


