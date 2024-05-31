# Use Ubuntu as the base image
FROM ubuntu:latest

# Install required packages
RUN apt-get update && \
    apt-get install -y \
    curl \
    ca-certificates \
    git \
    && rm -rf /var/lib/apt/lists/*

# Set the IMG_SHA256 environment variable
ENV IMG_SHA256="cc9bf08794353ef57b400d32cd1065765253166b0a09fba360d927cfbd158088"

# Download and verify the sha256sum
RUN curl -fSL "https://github.com/genuinetools/img/releases/download/v0.5.11/img-linux-amd64" -o "/usr/local/bin/img" \
    && echo "${IMG_SHA256}  /usr/local/bin/img" | sha256sum -c - \
    && chmod a+x "/usr/local/bin/img"

# Create the working directory and set premissions
RUN mkdir -p /workingdir && \
    chmod -R a+rwx /workingdir

# Download docker files
RUN git clone https://github.com/ldelaB2/Condor_Meta.git /workingdir