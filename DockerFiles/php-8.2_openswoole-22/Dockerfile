FROM ubuntu:22.04
ENV DEBIAN_FRONTEND noninteractive

RUN apt update && apt install -y wget pkg-config cmake git checkinstall

RUN apt update && apt install -y software-properties-common && add-apt-repository ppa:ondrej/php -y
RUN apt update && apt install -y software-properties-common && add-apt-repository ppa:openswoole/ppa -y
RUN apt update && apt install -y php8.2-openswoole php8.2-dev