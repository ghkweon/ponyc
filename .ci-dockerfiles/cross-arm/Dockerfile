FROM ponylang/ponyc-ci-x86-64-unknown-linux-gnu-builder:20191106

ARG CROSS_TRIPLE=arm-unknown-linux-gnueabi
ARG CROSS_CC=arm-linux-gnueabi-gcc
ARG CROSS_CXX=arm-linux-gnueabi-g++
ARG CROSS_CFLAGS=
ARG CROSS_CXXFLAGS=
ARG CROSS_LDFLAGS=
ARG CROSS_BITS=32
ARG CROSS_LINKER=arm-linux-gnueabi-gcc
ARG CROSS_TUNE=cortex-a9

USER root

RUN curl -L --output gcc-linearo.tar.xz "https://releases.linaro.org/components/toolchain/binaries/6.4-2018.05/arm-linux-gnueabi/gcc-linaro-6.4.1-2018.05-x86_64_arm-linux-gnueabi.tar.xz" \
 && tar xJf gcc-linearo.tar.xz -C /usr/local --strip 1 \
 && arm-linux-gnueabi-gcc --version \
 && rm gcc-linearo.tar.xz \
 && curl -L --output /usr/bin/qemu-arm-static https://github.com/multiarch/qemu-user-static/releases/download/v2.12.0/qemu-arm-static \
 && chmod +x /usr/bin/qemu-arm-static

RUN cmake --version

USER pony
WORKDIR /home/pony
