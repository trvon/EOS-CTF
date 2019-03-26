FROM debian:9.5

ARG SSH_MASTER_USER
ARG SSH_MASTER_PASS

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
 vim sudo openssh-server

COPY configs/ssh_config /etc/ssh/ssh_config
COPY configs/sshd_config /etc/ssh/sshd_config

COPY scripts/user.sh /usr/local/bin/user.sh
RUN chmod +x /usr/local/bin/user.sh
run /usr/local/bin/user.sh

COPY scripts/entrypoint.sh /usr/local/bin/entrypoint.sh
RUN chmod +x /usr/local/bin/entrypoint.sh

ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]

EXPOSE 22
CMD tail -f /dev/null
