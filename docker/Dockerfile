FROM ubuntu:22.04

# Non-interactive mode for apt-get
ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies
RUN apt-get update && \
    apt-get -y upgrade && \
    apt-get install -y \
    wget \
    curl \
    zlib1g-dev \
    libncurses5-dev \
    libbz2-dev \
    liblzma-dev \
    libcurl3-dev \
    libx11-xcb-dev \
    libxft-dev \
    libcurl4-openssl-dev \
    libboost-all-dev \
    clang \
    g++ \
    gcc \
    bzip2 \
    autoconf \
    tabix \
    pandoc \
    ca-certificates \
    software-properties-common \
    apt-transport-https \
    build-essential \
    libv8-dev \
    python3 \
    python3-pip \
    libgsl-dev \
    default-jdk \
    git \
    git-lfs \
    gradle \
    r-base \
    r-base-dev \
    make \
    xxd \
    openjdk-17-jdk

# Install git-lfs
RUN git lfs install

# Set the working directory
WORKDIR /src

# Install python dependencies
RUN curl -sSL https://bootstrap.pypa.io/get-pip.py -o get-pip.py
RUN python3 get-pip.py
RUN python3 -m pip install -U jinja2 pdfkit wkhtmltopdf

# Install wkhtmltopdf with QT patch
RUN wget https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6.1-2/wkhtmltox_0.12.6.1-2.jammy_amd64.deb && \
    apt-get install -y -f ./wkhtmltox_0.12.6.1-2.jammy_amd64.deb && \
    rm ./wkhtmltox_0.12.6.1-2.jammy_amd64.deb && \
    mv /usr/local/bin/wkhtmlto* /usr/bin/

# Install samtools
RUN wget https://github.com/samtools/samtools/releases/download/1.20/samtools-1.20.tar.bz2 && \
    tar xjf samtools-1.20.tar.bz2 && \
    rm samtools-1.20.tar.bz2 && \
    cd samtools-1.20 && \
    ./configure --prefix=/usr/local && \
    make && \
    make install

# Install STAR aligner 
RUN git clone https://github.com/alexdobin/STAR.git && \
    cd STAR/source && \
    make STAR

# Set up GATK
WORKDIR /src/GATK

RUN git clone https://github.com/broadinstitute/gatk.git && \
    cd gatk && \
    ./gradlew bundle
