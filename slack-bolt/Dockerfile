FROM node:14.15.3-alpine3.11
ENV APP_HOME /myapp
ENV PATH ${APP_HOME}/node_modules/.bin:$PATH
ENV TZ Asia/Tokyo
WORKDIR /myapp
RUN npm -v

RUN npm install
