# Fedora 25 Jenkins Slave
FROM fedora:25

RUN dnf install -y openssh-server java-1.8.0-openjdk sudo && dnf clean all
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd &&
    echo "jenkins ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

EXPOSE 22

RUN /usr/libexec/openssh/sshd-keygen rsa && \
  /usr/libexec/openssh/sshd-keygen ecdsa && \
  /usr/libexec/openssh/sshd-keygen ed25519
CMD ["/usr/sbin/sshd", "-D"]
