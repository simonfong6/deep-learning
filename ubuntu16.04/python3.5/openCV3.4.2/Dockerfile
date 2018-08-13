FROM simonfong6/deep-learning:9.0-cudnn7-devel-ubuntu16.04-python3.5

# Remove any previous installations of x264</h3>
RUN sudo apt-get remove x264 libx264-dev
 
# We will Install dependencies now
RUN sudo apt-get install -y build-essential checkinstall cmake pkg-config yasm \
    sudo apt-get install -y git gfortran \
    sudo apt-get install -y libjpeg8-dev libjasper-dev libpng12-dev
 
# More dependencies
RUN sudo apt-get install -y libtiff5-dev \
    sudo apt-get install -y libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev \
    sudo apt-get install -y libxine2-dev libv4l-dev \
    sudo apt-get install -y libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev \
    sudo apt-get install -y qt5-default libgtk2.0-dev libtbb-dev \
    sudo apt-get install -y libatlas-base-dev \
    sudo apt-get install -y libfaac-dev libmp3lame-dev libtheora-dev \
    sudo apt-get install -y libvorbis-dev libxvidcore-dev \
    sudo apt-get install -y libopencore-amrnb-dev libopencore-amrwb-dev \
    sudo apt-get install -y x264 v4l-utils

# Python depedencies
RUN pip install numpy scipy matplotlib scikit-image scikit-learn ipython

# OpenCV
RUN git clone https://github.com/opencv/opencv.git \
    cd opencv \
    git checkout 3.4.2 \
    cd ..

# OpenCV Contrib
RUN git clone https://github.com/opencv/opencv_contrib.git \
    cd opencv_contrib \
    git checkout 3.4.2 \
    cd ..

# Compile and install
RUN cd opencv \
    mkdir build \
    cd build \
    make -j4 \
    sudo make install \
    sudo sh -c 'echo "/usr/local/lib" >> /etc/ld.so.conf.d/opencv.conf' \
    sudo ldconfig \
