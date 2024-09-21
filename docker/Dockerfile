FROM ubuntu:22.04

# Install necessary packages
RUN apt-get update && apt-get install -y \
    git \
    build-essential \
    cmake \
    python3 \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory
WORKDIR /opt

# Clone the repository
RUN git clone --recursive https://github.com/nanoporetech/isONclust2.git

# Set the working directory to the cloned repository
WORKDIR /opt/isONclust2

# Create build directory
RUN mkdir build

# Set the working directory to the build directory
WORKDIR /opt/isONclust2/build

# Run cmake and make
RUN cmake .. 
RUN make -j 4

# add the binary to the PATH
ENV PATH="/opt/isONclust2/build/bin:${PATH}"