FROM centos

RUN yum -y install openssh-server

RUN useradd remote_user && \
    echo "remote_user:password" | chpasswd && \
    mkdir /home/remote_user/.ssh && \
    chmod 700 /home/remote_user/.ssh

COPY id_rsa.pub /home/remote_user/.ssh/authorized_keys

RUN chown remote_user:remote_user -R /home/remote_user/.ssh/ && \
    chmod 600 /home/remote_user/.ssh/authorized_keys

RUN ssh-keygen -A

EXPOSE 22

RUN rm -rf /run/nologin

CMD /usr/sbin/sshd -D