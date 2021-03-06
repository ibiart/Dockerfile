#+++++++++++++++++++++++++++++++++++++++
# Dockerfile for webdevops/php-apache-dev:alpine-3-php7
#    -- automatically generated  --
#+++++++++++++++++++++++++++++++++++++++

FROM webdevops/php-dev:alpine-3-php7

MAINTAINER info@webdevops.io
LABEL vendor=WebDevOps.io
LABEL io.webdevops.layout=8
LABEL io.webdevops.version=1.2.3

ENV WEB_DOCUMENT_ROOT  /app
ENV WEB_DOCUMENT_INDEX index.php
ENV WEB_ALIAS_DOMAIN   *.vm
ENV WEB_PHP_SOCKET  127.0.0.1:9000
ENV WEB_NO_CACHE_PATTERN  "\.(css|js|gif|png|jpg|svg|json|xml)$"

COPY conf/ /opt/docker/

# Install apache
RUN /usr/local/bin/apk-install \
        apache2 \
        apache2-utils \
        apache2-proxy \
        apache2-ssl \
	&& sed -ri ' \
		s!^(\s*CustomLog)\s+\S+!\1 /proc/self/fd/1!g; \
		s!^(\s*ErrorLog)\s+\S+!\1 /proc/self/fd/2!g; \
		' /etc/apache2/httpd.conf \
    && /opt/docker/bin/provision run --tag bootstrap --role webdevops-apache --role webdevops-php-apache --role webdevops-apache-dev --role webdevops-php-dev \
    && /opt/docker/bin/bootstrap.sh


EXPOSE 80 443
