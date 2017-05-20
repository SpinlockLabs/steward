# Alpine Linux Jenkins Slave
FROM alpine:3.5

RUN apk update && apk add openssh && rm -rf /var/cache/apk/*
RUN mkdir /home/jenkins && \
  addgroup -g 1001 jenkins && \
  adduser -u 1001 -G jenkins -h /home/jenkins -s /bin/sh -D jenkins && \
  chown -R jenkins:jenkins /home/jenkins && \
  echo "jenkins:jenkins" | chpasswd

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
