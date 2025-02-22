# Use a specific Alpine version
FROM alpine:3.18

# Install dependencies, download and build ExifTool
RUN apk add --no-cache perl curl make && \
    mkdir -p /app && \
    curl -o /app/exiftool.tar.gz -L https://github.com/exiftool/exiftool/archive/refs/tags/13.21.tar.gz && \
    tar xfz /app/exiftool.tar.gz -C /app && \
    cd /app/exiftool-13.17 && \
    perl Makefile.PL && \
    make && \
    make install && \
    apk del curl make && \
    rm -rf /app

# Set up the working directory and volume
VOLUME /source  # Mount point for files to be processed by ExifTool
WORKDIR /source

# Default command to run ExifTool interactively
CMD ["exiftool"]

