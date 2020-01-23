FROM alpine:3.9

ARG ssh_prv_key
ARG ssh_pub_key
ARG host_ip
ARG local_port
ARG remote_port
ARG host_user
ARG docker_root_path

RUN apk add --no-cache \
  openssh-client \
  ca-certificates \
  bash \
  autossh

RUN mkdir -p /root/.ssh && \
    chmod 0700 /root/.ssh && \
    ssh-keyscan $host_ip >> /root/.ssh/known_hosts && \
    echo "$ssh_prv_key" > /root/.ssh/id_rsa && \
    echo "$ssh_pub_key" > /root/.ssh/id_rsa.pub && \
    chmod 600 /root/.ssh/id_rsa && \
    chmod 600 /root/.ssh/id_rsa.pub

ENV HOST_IP=$host_ip
ENV LOCAL_PORT=$local_port
ENV REMOTE_PORT=$remote_port
ENV HOST_USER=$host_user

WORKDIR /usr/src/ssher
COPY ./$docker_root_path/entrypoint .

EXPOSE $local_port
EXPOSE $remote_port

CMD ["./entrypoint"]
