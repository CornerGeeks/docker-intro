FROM ubuntu:14.04
MAINTAINER Timothy Lim <tim@thewheatfield.org>
RUN apt-get update && apt-get install -y curl git
RUN curl -sL https://deb.nodesource.com/setup | sudo bash -
RUN apt-get update
RUN apt-get install -y nodejs
RUN npm install -g bower
RUN npm install -g gulp
RUN mkdir /slides
WORKDIR /slides
RUN git clone https://github.com/markdalgleish/presentation-tabs.git .
RUN npm install
RUN bower --allow-root install
CMD gulp serve
EXPOSE 8080 35729