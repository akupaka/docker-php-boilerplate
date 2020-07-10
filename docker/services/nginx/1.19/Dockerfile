FROM nginx:1.19
MAINTAINER Roman.K <akupaka@gmail.com>

RUN groupadd -g 1000 webapp \
 && useradd -g 1000 -u 1000 -d /var/www -s /bin/bash webapp
RUN touch /var/run/nginx.pid

RUN apt-get update && apt-get install -y \
    curl \
    libnss3-tools \
    openssl

RUN mkdir /etc/nginx/certs \
 && echo -e "\n\n\n\n\n\n\n" | openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/nginx/certs/nginx.key -out /etc/nginx/certs/nginx.crt

RUN cd /usr/local/bin/ \
 && curl -L https://github.com/FiloSottile/mkcert/releases/download/v1.4.1/mkcert-v1.4.1-linux-amd64 -o mkcert \
 && chmod +x mkcert

COPY ./conf/nginx.conf /etc/nginx/
COPY ./conf/default.conf /etc/nginx/conf.d/

RUN mkdir -p /var/www/default/public /var/www/default/uploads /sock \
 && chown -R webapp:webapp /var/www /etc/nginx /var/cache/nginx /var/run/nginx.pid /sock \ ;
# That does not seem to be working
# && find /var/www -type f -exec chmod 444 {} \;\
# && find /var/www -type d -exec chmod 555 {} \;\
# && chmod -R 644 /var/www/default/uploads

EXPOSE 8443

USER webapp:webapp

VOLUME /var/www

WORKDIR /var/www
