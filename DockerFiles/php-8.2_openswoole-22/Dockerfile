FROM ubuntu:22.04
ENV DEBIAN_FRONTEND noninteractive

RUN apt update && apt install -y wget pkg-config cmake git checkinstall

RUN apt update && apt install -y software-properties-common && add-apt-repository ppa:ondrej/php -y
RUN apt update && apt install -y software-properties-common && add-apt-repository ppa:openswoole/ppa -y
RUN apt update && apt install -y php8.2-openswoole php8.2-dev

# Lib `ffmpeg` for working with multimediagi files and streams
RUN apt update && apt install -y ffmpeg

# Build deb package
RUN wget https://raw.githubusercontent.com/php-opencv/php-opencv-packages/master/opencv_4.7.0_amd64.deb && dpkg -i opencv_4.7.0_amd64.deb && rm opencv_4.7.0_amd64.deb
RUN git clone https://github.com/php-opencv/php-opencv.git

# Install OpenCV
RUN cd php-opencv && phpize && ./configure --with-php-config=/usr/bin/php-config && make
RUN cd php-opencv && checkinstall --default --type debian --install=no --pkgname php-opencv --pkgversion "8.2-4.7.0" --pkglicense "Apache 2.0" --pakdir ~ --maintainer "php-opencv" --addso --autodoinst make install && make test