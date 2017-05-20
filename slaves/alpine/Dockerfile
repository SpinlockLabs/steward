# Alpine Linux Jenkins Slave
FROM openjdk:8-jdk-alpine

RUN apk update && apk add openssh bash git sudo && rm -rf /var/cache/apk/*
RUN mkdir /home/jenkins && \
  addgroup -g 1001 jenkins && \
  adduser -u 1001 -G jenkins -h /home/jenkins -s /bin/sh -D jenkins && \
  chown -R jenkins:jenkins /home/jenkins && \
  echo "jenkins:jenkins" | chpasswd && \
  echo "jenkins ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N '' && \
  ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key -N '' && \
  ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key -N '' && \
  ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key -N ''

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
