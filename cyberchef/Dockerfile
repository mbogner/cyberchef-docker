FROM alpine:latest as unzipper
RUN apk add --no-cache unzip
ENV CYBERCHEF_VERSION=10.4.0
ADD https://github.com/gchq/CyberChef/releases/download/v$CYBERCHEF_VERSION/CyberChef_v$CYBERCHEF_VERSION.zip /data/
RUN mkdir /data/out && unzip /data/CyberChef_v$CYBERCHEF_VERSION.zip -d /data/out/

FROM nginx:alpine
LABEL org.opencontainers.image.authors="clayey-radios-0j@icloud.com"
ENV CYBERCHEF_VERSION=10.4.0
RUN rm -rf /usr/share/nginx/html/*
COPY --from=unzipper /data/out/ /usr/share/nginx/html/
RUN ln -s /usr/share/nginx/html/CyberChef_v$CYBERCHEF_VERSION.html /usr/share/nginx/html/index.html
EXPOSE 80