FROM node:lts

RUN apt-get update -y

WORKDIR /root

RUN npm install -D \
	webpack webpack-cli \
	vue vue-loader vue-template-compiler

ENV PATH /root/node_modules/.bin:${PATH}

WORKDIR /root/app
