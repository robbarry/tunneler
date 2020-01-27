FROM alpine:3.9

ARG docker_root_path
ARG host_ip

RUN apk add --no-cache \
  openssh-client \
  ca-certificates \
  bash \
  autossh

RUN mkdir -p /root/.ssh && \
    chmod 0700 /root/.ssh && \    
    ssh-keygen -q -t rsa -N '' -f root/.ssh/id_rsa && \
    ssh-keyscan $host_ip >> /root/.ssh/known_hosts

WORKDIR /usr/src/ssher
COPY ./$docker_root_path/entrypoint .

ENV host_ip=$host_ip

CMD ["./entrypoint"]

RUN output="$( echo SHARE THIS KEY WITH YOUR ADMIN: && \
               cat /root/.ssh/id_rsa.pub)" && echo $output