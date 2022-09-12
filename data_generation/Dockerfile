FROM ubuntu:xenial-20210804
ENV LD_LIBRARY_PATH=/lib:/usr/lib:/usr/local/lib
RUN apt-get update &&\
    apt-get install -y --no-install-recommends g++ \
    cmake \
    wget \
    unzip \
    git \
    libglib2.0-dev\
    cmake\
    openjdk-8-jdk\
    python-dev\
    python-gtk2\
    libgtk2.0-dev\
    mesa-common-dev\
    libgl1-mesa-dev\
    libglu1-mesa-dev\
    freeglut3-dev\
    libjpeg-dev\
    build-essential\
    libglib2.0-dev\
    libcanberra-gtk-module\
    libcanberra-gtk3-module &&\
    wget -O lcm.zip "https://api.github.com/repos/lcm-proj/lcm/zipball/v1.4.0" &&\
    unzip lcm.zip &&\
    cd /lcm-proj-lcm-abc18a8 &&\
    mkdir build && cd build &&\
    cmake .. &&\
    make -j 4 &&\
    make install &&\
    git clone "https://github.com/libbot2/libbot2.git" &&\
    cd libbot2 &&\
    make -j 4 BUILD_PREFIX=/usr/local
WORKDIR /data_generation
COPY ./ ./
RUN make
RUN ls build/bin