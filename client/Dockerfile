FROM node:alpine as todo-app-build

WORKDIR /client

COPY package.json yarn.lock README.md ./

RUN yarn

COPY ./public ./public

COPY ./src ./src

#ENV REACT_APP_baseAPIURL=<backend-app-service-ip>:<port>
ENV REACT_APP_baseAPIURL=192.168.49.2:30756

RUN yarn build

FROM nginx:latest

LABEL maintainer=Aamir-Pinger

COPY --from=todo-app-build /client/build/ /usr/share/nginx/html

EXPOSE 80
