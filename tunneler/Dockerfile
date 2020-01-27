FROM alpine:3.9

ARG docker_root_path
ARG host_ip

RUN apk add --no-cache \
  openssh-client \
  ca-certificates \
  bash \
  autossh

COPY certs/tunneler_rsa /root/.ssh/id_rsa
COPY certs/tunneler_rsa.pub /root/.ssh/id_rsa.pub

RUN chmod 0700 /root/.ssh    

WORKDIR /usr/src/tunneler
COPY ./$docker_root_path/entrypoint .

ENV host_ip=$host_ip

CMD ["./entrypoint"]