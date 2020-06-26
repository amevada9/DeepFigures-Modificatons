# image for running DeepFigures

FROM tensorflow/tensorflow:1.15.0-py3

ENV LC_ALL C.UTF-8

# Turn off Debian frontend
# Having this fueature on causes issues on windows computers

ENV DEBIAN_FRONTEND=noninteractive


# install system packages


RUN apt-get clean \
 && apt-get update --fix-missing \
 && apt-get install -y \
    git \
    curl \
    gcc \
    build-essential \
    tcl \
    g++ \
    zlib1g-dev \
    libjpeg8-dev \
    libtiff5-dev \
    libpng-dev \
    tcl-dev \
    tk-dev \
    python3 \
    python3-pip \
    python3-tk \
    ghostscript \
    openjdk-8-jre \
    poppler-utils \
    texlive-latex-base \
    texlive-fonts-recommended \
    texlive-fonts-extra \
    texlive-latex-extra

WORKDIR /work

# install python packages

ADD ./requirements.txt /work

RUN pip3 install --upgrade pip \
 && pip install Cython==0.25.2
RUN pip3 install -r ./requirements.txt

ADD ./vendor/tensorboxresnet /work/vendor/tensorboxresnet
RUN pip3 install -e /work/vendor/tensorboxresnet

ADD . /work
RUN pip3 install --quiet -e /work

CMD [ "/bin/bash" ]
