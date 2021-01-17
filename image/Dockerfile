FROM ubuntu:latest
LABEL maintainer="Michael Uman"
ENV TZ="America/Los_Angeles"
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt update && apt install -y openssh-server python3 \
  python3-pip gcc sudo cmake vim tree htop iputils-ping \
  mc  && rm -rf /var/lib/apt/lists/* && pip3 install numpy \
  scipy matplotlib ipython jupyter pandas sympy nose
RUN useradd -rm -d /home/developer -s /bin/bash -g root -G sudo developer
RUN echo 'developer:developer' | chpasswd
RUN ssh-keygen -A -v
RUN update-rc.d ssh defaults
EXPOSE 22
ENTRYPOINT service ssh restart && bash
