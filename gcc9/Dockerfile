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
        g++ \
    && groupadd 1001 -g 1001 \
    && groupadd 1000 -g 1000 \
    && groupadd 2000 -g 2000 \
    && groupadd 999 -g 999 \
    && useradd -ms /bin/bash conan -g 1001 -G 1000,2000,999 \
    && printf "conan:conan" | chpasswd \
    && adduser conan sudo \
    && printf "conan ALL= NOPASSWD: ALL\\n" >> /etc/sudoers

USER conan

RUN sudo pip3 install -q --no-cache-dir \
        conan

WORKDIR /home/conan

