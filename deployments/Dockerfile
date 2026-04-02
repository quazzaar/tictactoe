FROM node:8.15.1-alpine

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

WORKDIR /app
ADD ./ /app

RUN chown -R appuser:appgroup /app
RUN npm config set unsafe-perm true
RUN apk update && \
    npm install --production package.json && \
    npm install -g gulp@3.9.1

USER appuser
CMD gulp && node src/app.js
