FROM ubuntu

LABEL maintainer="ben@yarm.is"

# Run updates and install base libs & tools
RUN apt-get -y update                  \
 && apt-get -y install cmake           \
                       build-essential \
                       libjpeg8-dev    \
                       imagemagick     \
                       libv4l-dev      \
                       git             \
 && rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/jacksonliam/mjpg-streamer.git \
 && cd mjpg-streamer/mjpg-streamer-experimental                \
 && make                                                       \
 && make install \
 && cd /

RUN echo "#!/bin/bash" >> start.sh \
 && echo "export LD_LIBRARY_PATH=\"/mjpg-streamer/mjpg-streamer-experimental\"" >> start.sh \
 && echo "/mjpg-streamer/mjpg-streamer-experimental/mjpg_streamer --input \"/mjpg-streamer/mjpg-streamer-experimental/input_uvc.so\" --output \"/mjpg-streamer/mjpg-streamer-experimental/output_http.so\"" >> start.sh \
 && chmod +x start.sh

EXPOSE 8080

ENTRYPOINT ["/start.sh", "output_http.so -w ./www"]

