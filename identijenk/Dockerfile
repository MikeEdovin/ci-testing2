FROM jenkins/jenkins:lts
USER root

RUN echo "https://download.docker.com/linux/debian/dists/jessie/Release" \
      && apt-key adv --keyserver keyserver.ubuntu.com \
          --recv-keys 58118E89F3A912897C070ADBF76221572C52609D \
      && apt-get update \
      && apt-get install -y apt-transport-https \
      && apt-get install -y sudo \
      && apt-get install -y docker.io \
      && rm -rf /var/lib/apt/lists/*
RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

RUN curl -L https://github.com/docker/compose/tree/v2/pkg/compose/\
docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose; \
    chmod +x /usr/local/bin/docker-compose

USER jenkins
#new way to install pluging instead of plugin.sh+plugin.txt
RUN jenkins-plugin-cli --plugins scm-api:631.v9143df5b_e4a_a
RUN jenkins-plugin-cli --plugins git-client:3.13.1
RUN jenkins-plugin-cli --plugins git:4.14.3

