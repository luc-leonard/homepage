FROM klakegg/hugo:0.80.0-ext-alpine AS builder
COPY ./homepage /website
WORKDIR /website
RUN hugo

FROM flashspys/nginx-static:latest
COPY --from=builder "/website/public" "/app"
RUN chmod -R 777 /app
