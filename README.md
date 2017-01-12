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

    tar -xvf <filename>.tgz
    sudo cp cuda/include/*.h /usr/local/cuda/include
    sudo cp cuda/lib64/*.so* /usr/local/cuda/lib64

###Anaconda2.4

Go to https://www.continuum.io/downloads
    
    bash <filename>.sh

###OpenCV 3.1

Go to http://webnautes.tistory.com/1030

    sudo apt-get install build-essential checkinstall cmake git pkg-config yasm libtiff5-dev libjpeg-dev libjasper-dev libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev libxine2-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev  libv4l-dev python-dev python-numpy libtbb-dev libgtk2.0-dev libfaac-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev x264 v4l-utils libopenexr-dev python-tk  libeigen3-dev libx264-dev

    sudo add-apt-repository ppa:mc3man/gstffmpeg-keep
    sudo apt-get update
    sudo apt-get install ffmpeg gstreamer0.10-ffmpeg

Download OpenCV source code

    mkdir opencv_source
    cd opencv_source
    git clone https://github.com/Itseez/opencv.git
    git clone https://github.com/Itseez/opencv_contrib.git

Setup OpenCV

    cd opencv
    mkdir build
    cd build
    cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr \
    -D BUILD_NEW_PYTHON_SUPPORT=ON -D WITH_V4L=ON \
    -D WITH_TBB=ON -D WITH_IPP=OFF \
    -DOPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules  ../ 

Compile OpenCV & Install

    make  -j $(nproc)
    sudo make install
    sudo ldconfig

Check version

    pkg-config --modversion opencv

If version is 2.4.9.1, remove past opencv2.4

    sudo apt-get autoremove opencv-doc opencv-data libopencv-dev libopencv2.4-java libopencv2.4-jni python-opencv libopencv-core2.4 libopencv-gpu2.4 libopencv-ts2.4 libopencv-photo2.4 libopencv-contrib2.4 libopencv-imgproc2.4 libopencv-superres2.4 libopencv-stitching2.4 libopencv-ocl2.4 libopencv-legacy2.4 libopencv-ml2.4 libopencv-video2.4 libopencv-videostab2.4 libopencv-objdetect2.4 libopencv-calib3d2.4


##References

1. http://blog.daum.net/_blog/BlogTypeView.do?blogid=0fjLE&articleno=28&categoryId=7&regdt=20161224170447

2. http://www.whydsp.org/316

3. http://webnautes.tistory.com/1030
