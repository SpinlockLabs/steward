# Fedora 25 Jenkins Slave
FROM fedora:25

RUN dnf install -y openssh-server && dnf clean all
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

EXPOSE 22

RUN /usr/libexec/openssh/sshd-keygen rsa && \
  /usr/libexec/openssh/sshd-keygen ecdsa && \
  /usr/libexec/openssh/sshd-keygen ed25519
CMD ["/usr/sbin/sshd", "-D"]
