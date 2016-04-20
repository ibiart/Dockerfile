#+++++++++++++++++++++++++++++++++++++++
# Dockerfile for webdevops/php-dev:alpine-3
#    -- automatically generated  --
#+++++++++++++++++++++++++++++++++++++++

FROM webdevops/php:alpine-3

MAINTAINER info@webdevops.io
LABEL vendor=WebDevOps.io
LABEL io.webdevops.layout=6
LABEL io.webdevops.version=0.23.0

COPY conf/ /opt/docker/

# Install tools
RUN /usr/local/bin/apk-install \
        graphviz \
    && /opt/docker/bin/provision-run.sh webdevops-php-dev \
    && /opt/docker/bin/bootstrap.sh
