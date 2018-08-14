FROM simonfong6/deep-learning:9.0-cudnn7-devel-ubuntu16.04-python3.5

# Remove any previous installations of x264</h3>
RUN apt-get remove x264 libx264-dev
 
# We will Install dependencies now
RUN apt-get install -y build-essential checkinstall cmake pkg-config yasm && \
    apt-get install -y git gfortran && \
    apt-get install -y libjpeg8-dev libjasper-dev libpng12-dev
 
# More dependencies
RUN apt-get install -y libtiff5-dev && \
    apt-get install -y libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev && \
    apt-get install -y libxine2-dev libv4l-dev && \
    apt-get install -y libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev && \
    apt-get install -y qt5-default libgtk2.0-dev libtbb-dev && \
    apt-get install -y libatlas-base-dev && \
    apt-get install -y libfaac-dev libmp3lame-dev libtheora-dev && \
    apt-get install -y libvorbis-dev libxvidcore-dev && \
    apt-get install -y libopencore-amrnb-dev libopencore-amrwb-dev && \
    apt-get install -y x264 v4l-utils

# Python depedencies
RUN pip3 install numpy scipy matplotlib scikit-image scikit-learn ipython

# Set OpenCV version.
ENV OPENCV_VERSION 3.4.2

# OpenCV
RUN git clone https://github.com/opencv/opencv.git && \
    cd opencv && \
    git checkout $OPENCV_VERSION && \
    cd ..

# OpenCV Contrib
RUN git clone https://github.com/opencv/opencv_contrib.git && \
    cd opencv_contrib && \
    git checkout $OPENCV_VERSION && \
    cd ..

# Compile and install
RUN cd opencv && \
    mkdir build && \
    cd build && \
    make -j4 && \
    make install && \
    sh -c 'echo "/usr/local/lib" >> /etc/ld.so.conf.d/opencv.conf' && \
    ldconfig && \
