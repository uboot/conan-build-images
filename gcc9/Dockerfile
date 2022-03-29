FROM ubuntu:20.04

RUN DEBIAN_FRONTEND=noninteractive apt-get -qq update \
    && apt -qq install -y tzdata

RUN apt-get -qq install -y --no-install-recommends \
        sudo \
        python3-pip \
        gcc \
        cmake \
        ssh-client \
        git \
        make \
        g++
RUN groupadd conan \
    && useradd -ms /bin/bash conan -g conan \
    && printf "conan:conan" | chpasswd \
    && adduser conan sudo \
    && printf "conan ALL= NOPASSWD: ALL\\n" >> /etc/sudoers

USER conan

RUN sudo pip3 install -q --no-cache-dir \
        conan

WORKDIR /home/conan
