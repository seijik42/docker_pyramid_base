FROM ubuntu:14.04
MAINTAINER seijik42

RUN locale-gen en_US.UTF-8  
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8  

# build python environment

RUN apt-get -qq update && apt-get -qq install -y \
    git \
    python3.4 \
    python3-pip
RUN rm -f /usr/bin/python \
    && rm -f /usr/bin/python \
    && ln -s /usr/bin/python3.4 /usr/bin/python \
    && ln -s /usr/bin/pip3 /usr/bin/pip

# create pyramid project

WORKDIR /opt/
RUN pip -q install pyramid waitress && pcreate -s starter app
WORKDIR /opt/app
 
ONBUILD COPY . /opt/app
ONBUILD RUN [ -f "requirement.txt" ] && pip -q install -r requirement.txt || echo "requirements.txt not exist" 
ONBUILD RUN python setup.py develop
EXPOSE 6543
