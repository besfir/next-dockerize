FROM node:18.16.0-alpine3.17

WORKDIR /next-app
RUN apk add --no-cache libc6-compat && \
    apk --no-cache add tzdata && \
    cp /usr/share/zoneinfo/Asia/Seoul /etc/localtime && \
    echo "Asia/Seoul" > /etc/timezone
