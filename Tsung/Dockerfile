# Inspired from : 
#   * https://docs.docker.com/examples/running_ssh_service/
#   * https://github.com/datawrangling/ec2cluster/issues/35
#
# To be improved in Ubuntu 12.04. Erlang version mismatch in 14.04

FROM ubuntu:12.04
MAINTAINER Foucault de Bonneva <foucault@commit.ninja>

ADD start-bench /usr/sbin
ADD tsung.xml /root/.tsung

RUN chmod +x /usr/sbin/start-bench
RUN apt-get update && apt-get install -y openssh-server tsung
RUN mkdir /var/run/sshd
RUN mkdir /root/.tsung

RUN ssh-keygen -b 1024 -N '' -f ~/.ssh/id_dsa -t dsa -q
RUN cat /root/.ssh/id_dsa.pub > /root/.ssh/authorized_keys


VOLUME ["/root/.tsung/log"]

CMD ["/usr/sbin/start-bench"]
