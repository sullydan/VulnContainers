FROM alpine:3.21

RUN apk update && apk add docker openrc openssh openssh-server openssh-client libcap && \
    mkdir /run/sshd && \
    ssh-keygen -A && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config && \
    echo "root:hackersnhops" | chpasswd

EXPOSE 22

COPY key /root/key

RUN rc-update add docker boot

CMD ["/usr/sbin/sshd", "-D"]