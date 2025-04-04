FROM ubuntu:22.04

RUN apt-get update && apt-get install -y openssh-server

RUN useradd remote_user && echo "remote_user:1234" | chpasswd && \
    mkdir /home/remote_user/.ssh -p && \
    chmod 700 /home/remote_user/.ssh && \
    mkdir -p  -m0755 /var/run/sshd

COPY key.pub /home/remote_user/.ssh/authorized_keys

RUN chmod 400 /home/remote_user/.ssh/authorized_keys && \
    chown -R remote_user:remote_user /home/remote_user/

CMD ["/usr/sbin/sshd", "-D"]