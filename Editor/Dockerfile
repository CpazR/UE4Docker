# Unreal Engine 4 Build container
#
# VERSION               4.8.0

FROM centos:centos7

RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-Base.repo && \
    sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-Base.repo && \
    yum clean all && \
    yum update -y && \
    yum install -y \
        ninja-build \
        python3 \
        libxcb \
        libxcb-devel \
        xcb-util \
        xcb-util-devel \
        autoconf \
        git \
        curl \
        bison \
        flex \
        dos2unix \
        cmake \
        unzip \
        gcc \
        wget \
        redhat-lsb-core \
        gtk3-devel \
        gtk2-devel \
        qt-devel \
        libstdc++-devel \
        gcc-c++ \
        clang \
        libX11-devel \
        libXext-devel \
        mesa-libGL-devel \
        pulseaudio-libs-devel \
        alsa-lib-devel \
        libXcursor-devel \
        libXi-devel \
        libXinerama-devel \
        libXrandr-devel \
        mono-core \
        mono-complete \
        mono-devel \
        dotnet-sdk-3.1 \
    && yum clean all

RUN mkdir -p /root/UnrealEngine/Engine/Extras/ThirdPartyNotUE/SDKs/HostLinux/Linux_x64 && \
    cd /root/UnrealEngine/Engine/Extras/ThirdPartyNotUE/SDKs/HostLinux/Linux_x64 && \
    wget https://cdn.unrealengine.com/Toolchain_Linux/native-linux-v19_clang-11.0.1-centos7.tar.gz && \
    tar -xzf native-linux-v19_clang-11.0.1-centos7.tar.gz && \
    rm native-linux-v19_clang-11.0.1-centos7.tar.gz

COPY build.sh /root/build.sh

RUN dos2unix /root/build.sh && \
    chmod +x /root/build.sh

ENV BUILD Editor
ENV HOME /root
ENV DOTNET_CLI_TELEMETRY_OPTOUT=1
ENV DOTNET_SKIP_FIRST_TIME_EXPERIENCE=1

CMD ["bash", "/root/build.sh"]


