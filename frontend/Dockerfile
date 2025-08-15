# Force Build 8
FROM node:alpine3.22 AS build

RUN apk add git
RUN git clone https://github.com/pxlsspace/pxls-web.git
WORKDIR /pxls-web
RUN npm install
RUN npm run build

FROM node:alpine3.22
LABEL maintainer="Aneurin Price adp@nyeprice.space"
RUN mkdir /frontend
COPY --from=build /pxls-web /frontend
COPY config.json5 /frontend/config.json5
WORKDIR /frontend
ENTRYPOINT [ "npm", "start" ]
