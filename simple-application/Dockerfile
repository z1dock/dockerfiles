# syntax=docker/dockerfile:1
FROM node:12-alpine

RUN apk add --no-cache python2 g++ make
WORKDIR /app
COPY app .
# COPY app/package.json app/yarn.lock ./
# COPY app/spec ./spec

RUN yarn install --production
CMD ["node", "src/index.js"]
