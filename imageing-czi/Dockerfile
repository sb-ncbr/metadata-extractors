FROM alpine:3.20

RUN apk -Uuv add openjdk8-jre \
  && mkdir -p /opt /data \
  && wget http://downloads.openmicroscopy.org/latest/bio-formats/artifacts/bftools.zip \
  && unzip bftools.zip -x '*.bat' -d /opt/ \
  && rm /var/cache/apk/* /bftools.zip

ENV PATH $PATH:/opt/bftools/

WORKDIR /data
