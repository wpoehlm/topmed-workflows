FROM ubuntu:bionic

RUN apt-get update && apt-get install -y \
   sudo \
   gcc \
   nano \
   cmake \
   git \
   wget \
   python \
   build-essential \
   zlib1g-dev \
   libcurl4-gnutls-dev \
   liblzma-dev \
   libbz2-dev \
   libssl-dev \
   autoconf

RUN wget https://github.com/samtools/htslib/releases/download/1.3.2/htslib-1.3.2.tar.bz2 -O htslib.tar.bz2 
RUN tar -xjvf htslib.tar.bz2 
RUN cd htslib-1.3.2/ && make

ENV PATH="$PATH:/htslib-1.3.2"

RUN git clone https://github.com/Griffan/VerifyBamID.git
RUN cd VerifyBamID && mkdir build && cd build/ && cmake .. && make && make test
RUN export PATH=$PATH:/VerifyBamID/bin/  

COPY Dockerfile /opt/
