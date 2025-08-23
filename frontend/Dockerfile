# Force Build 8
FROM node:alpine3.22 AS build

RUN apk add git

WORKDIR /pxls-web

COPY ./pxls-web/package*.json ./

RUN --mount=type=cache,target=/app/npm/cache \
    npm install --cache /app/npm/cache --loglevel error --frozen-lockfile

COPY ./pxls-web /pxls-web

RUN npm run build

COPY config.json5 /pxls-web/config.json5
ENTRYPOINT [ "npm", "start" ]
EXPOSE 3000
