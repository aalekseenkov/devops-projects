FROM ubuntu:latest

ARG USER=${USER}

# Add sudo and openssh-server
ENV DEBIAN_FRONTEND=noninteractive
RUN apt update && apt install openssh-server sudo -y

# Setup running user on the container with sudo rights and
# password-less ssh login
RUN if [ "${USER}" != "root" ]; then \
  useradd -m ${USER} && \
  adduser ${USER} sudo && \
  echo "${USER} ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/sudoers; \
fi

# As the user setup the ssh identity using the key in the tmp folder
USER "${USER}"
RUN mkdir ~/.ssh && chmod -R 700 ~/.ssh
COPY id_rsa.pub /tmp/id_rsa.pub
RUN cat /tmp/id_rsa.pub >> ~/.ssh/authorized_keys
RUN chmod 644 ~/.ssh/authorized_keys

# start ssh with port exposed
USER root
RUN service ssh start

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
