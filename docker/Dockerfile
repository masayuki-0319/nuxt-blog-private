FROM node:13.2.0-alpine3.10
ENV LANG C.UTF-8
ENV TZ Asia/Tokyo

RUN apk update && \
    apk upgrade && \
    apk add --no-cache git vim less python make g++

ARG YARN_VERSION=1.19.1
RUN npm install --global npm yarn@$YARN_VERSION && \
    chmod +x /usr/local/bin/yarn && \
    yarn install

RUN yarn global add @vue/cli create-nuxt-app

WORKDIR /src
EXPOSE 3000