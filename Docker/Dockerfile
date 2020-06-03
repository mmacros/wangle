#Pull base image
FROM ubuntu
LABEL maintainer="mmacros@gmail.com"
#Install libs and dev enviroment
ENV TZ=America/Argentina/Buenos_Aires
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update -y && \ 
    apt-get install \
        g++ \
        cmake \
        libboost-all-dev \
        libevent-dev \
        libdouble-conversion-dev \
        libgoogle-glog-dev \
        libgflags-dev \
        libiberty-dev \
        liblz4-dev \
        liblzma-dev \
        libsnappy-dev \
        make \
        zlib1g-dev \
        binutils-dev \
        libjemalloc-dev \
        libssl-dev \
        pkg-config \
        libunwind-dev \
        libunwind8-dev \
        libelf-dev \
        libdwarf-dev \
        libsodium-dev \
        wget \
        git \
        -y
#Install dependency
#googletest        
RUN wget https://github.com/google/googletest/archive/release-1.8.0.tar.gz && \
    tar zxf release-1.8.0.tar.gz && \
    rm -f release-1.8.0.tar.gz && \
    cd googletest-release-1.8.0 && \
    cmake . && \
    make && \
    make install && \
    cd ..
#fmt
RUN git clone https://github.com/fmtlib/fmt.git && \
    cd fmt && \
    mkdir _build && cd _build && \
    cmake .. && \
    make -j$(nproc) && \
    make install && \
    cd ../..
#folly
RUN git clone https://github.com/facebook/folly && \
    mkdir folly/_build && cd folly/_build && \
    cmake .. && \
    make -j $(nproc) && \
    make install && \
    cd ../..
#fizz
RUN git clone https://github.com/facebookincubator/fizz && \ 
    mkdir fizz/_build && cd fizz/_build && \
    cmake ../fizz && \
    make -j $(nproc) && \
    make install && \
    cd ../..
#wangle
RUN git clone https://github.com/facebook/wangle && \ 
    mkdir wangle/_build && cd wangle/_build && \
    cmake ../wangle && \
    make -j $(nproc) && \
    make install && \
    cd ../..
CMD ["/bin/bash"]
WORKDIR  /workdir
VOLUME ["/workdir"]

