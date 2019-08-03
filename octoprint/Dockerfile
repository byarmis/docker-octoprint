FROM python:2.7
EXPOSE 5000
LABEL maintainer="ben@yarm.is"


WORKDIR /opt/octoprint

#install ffmpeg
RUN wget -O ffmpeg.tar.xz https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-i686-static.tar.xz \
 && mkdir -p /opt/ffmpeg                                                                              \
 && tar xvf ffmpeg.tar.xz -C /opt/ffmpeg --strip-components=1                                         \
 && rm ffmpeg.tar.xz

#Create an octoprint user
RUN useradd -ms /bin/bash octoprint \
 && adduser octoprint dialout
RUN chown octoprint:octoprint /opt/octoprint
USER octoprint
#This fixes issues with the volume command setting wrong permissions
RUN mkdir /home/octoprint/.octoprint

#Install Octoprint
RUN git clone --branch master https://github.com/foosel/OctoPrint.git /opt/octoprint \
 && virtualenv venv                                                                  \
 && ./venv/bin/python setup.py install

VOLUME /home/octoprint/.octoprint

CMD ["/opt/octoprint/venv/bin/octoprint", "serve"]

