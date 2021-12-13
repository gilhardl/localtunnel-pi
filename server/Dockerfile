FROM --platform=linux/arm/v7 node:10-alpine

WORKDIR /app

RUN apk update && apk upgrade && \
    apk add --no-cache git

RUN git clone https://github.com/localtunnel/server .

RUN yarn install --production && yarn cache clean

ENV NODE_ENV=production

ENTRYPOINT ["node", "-r", "esm", "./bin/server"]
