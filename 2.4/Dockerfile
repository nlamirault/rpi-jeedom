# VERSION:        2.4
# AUTHOR:         Nicolas Lamirault <nicolas.lamirault@gmail.com>
# DESCRIPTION:    zeiot/rpi-jeedom

FROM resin/armv7hf-debian:jessie
MAINTAINER Nicolas Lamirault <nicolas.lamirault@gmail.com>

ENV JEEDOM_VERSION 2.4

RUN apt-get update && apt-get install -y unzip

ADD https://github.com/jeedom/core/archive/${JEEDOM_VERSION}.zip /jeedom.zip

RUN unzip /jeedom.zip
RUN mv /core-${JEEDOM_VERSION} /jeedom && \
    rm /jeedom.zip

ENV SHELL_ROOT_PASSWORD Mjeedom96

RUN apt-get update && apt-get install -y wget openssh-server supervisor mysql-client

RUN echo "root:${SHELL_ROOT_PASSWORD}" | chpasswd && \
  sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
  sed -i 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' /etc/pam.d/sshd

WORKDIR "/jeedom"

RUN mkdir -p /var/run/sshd /var/log/supervisor
RUN cp install/motd /etc/motd && \
    cp install/bashrc /root/.bashrc && \
    cp install/OS_specific/Docker/supervisord.conf /etc/supervisor/conf.d/supervisord.conf && \
    cp install/install.sh /root/install_docker.sh && \
    chmod +x /root/install_docker.sh
RUN /root/install_docker.sh -s 1 -v ${JEEDOM_VERSION};exit 0
RUN /root/install_docker.sh -s 2 -v ${JEEDOM_VERSION};exit 0
RUN /root/install_docker.sh -s 4 -v ${JEEDOM_VERSION};exit 0
RUN /root/install_docker.sh -s 5 -v ${JEEDOM_VERSION};exit 0
RUN /root/install_docker.sh -s 7 -v ${JEEDOM_VERSION};exit 0
RUN /root/install_docker.sh -s 10 -v ${JEEDOM_VERSION};exit 0

# RUN cp install/OS_specific/Docker/init.sh /root/init.sh && \
#     chmod +x /root/init.sh

# EXPOSE 22 8080

# CMD ["/root/init.sh"]

# VOLUME ["/config"]
