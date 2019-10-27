FROM node:lts

RUN apt-get update -y

WORKDIR /root

RUN npm install -D @vue/cli

ENV PATH /root/node_modules/.bin:${PATH}

WORKDIR /root/vue
