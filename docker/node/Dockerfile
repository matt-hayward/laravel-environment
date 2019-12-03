FROM node:8.16.0

RUN apt-get update && apt-get install -y vim

RUN mkdir /root/.ssh
RUN chmod -R 0775 /root/.ssh

RUN ssh-keyscan bitbucket.org >> /root/.ssh/known_hosts
